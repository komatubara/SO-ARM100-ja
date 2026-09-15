---
title: データ収集と学習
eyebrow: Hugging Face チュートリアル
lead: 組み立てと校正が終わったあとの本編です。テレオペ、データ記録、ACT の学習、実機での推論まで、Hugging Face の実機模倣学習ガイドを日本語にしています。
---

<p class="source-note">非公式訳です。原本は <a href="https://huggingface.co/docs/lerobot/il_robots">huggingface.co/docs/lerobot/il_robots</a>。コマンドは SO-101 向けに寄せています。ポートと <code>id</code> は自分の環境に置き換えてください。</p>

このチュートリアルでは、実機を自律制御するニューラルネットワークの育て方を説明します。

1. データセットを記録し、可視化する
2. そのデータでポリシーを学習し、評価の準備をする
3. ポリシーを評価し、結果を見る

例として、レゴブロックをつかんで箱に入れる、といった作業を高い成功率で再現できるようになります。

<video controls playsinline>
  <source src="https://huggingface.co/datasets/huggingface/documentation-images/resolve/main/lerobot/lerobot_task.mp4" type="video/mp4">
</video>

データ収集では、リーダーアームなどのテレオペ装置でロボットを動かし、軌道を記録します。十分な軌道が集まったら、それを模倣するネットワークを学習し、実機に載せます。

コマンドをまとめて出したい場合は、公式の [quickstart notebook](https://github.com/huggingface/lerobot/blob/main/examples/notebooks/quickstart.ipynb) もあります。

組み立てと校正がまだなら、先に [組み立て]({{ '/assembly/' | relative_url }}) を終えてください。

## テレオペレーション

`id` は校正ファイルの保存名です。テレオペ・記録・評価で **同じ `id`** を使ってください。

```bash
lerobot-teleoperate \
    --robot.type=so101_follower \
    --robot.port=/dev/ttyACM0 \
    --robot.id=my_awesome_follower_arm \
    --teleop.type=so101_leader \
    --teleop.port=/dev/ttyACM1 \
    --teleop.id=my_awesome_leader_arm
```

```python
from lerobot.teleoperators.so_leader import SO101Leader, SO101LeaderConfig
from lerobot.robots.so_follower import SO101Follower, SO101FollowerConfig

robot_config = SO101FollowerConfig(
    port="/dev/ttyACM0",
    id="my_follower_arm",
)
teleop_config = SO101LeaderConfig(
    port="/dev/ttyACM1",
    id="my_leader_arm",
)

robot = SO101Follower(robot_config)
teleop_device = SO101Leader(teleop_config)
robot.connect()
teleop_device.connect()

while True:
    action = teleop_device.get_action()
    robot.send_action(action)
```

このコマンドは、欠けている校正があれば校正を始め、ロボットと操作装置をつないでテレオペを開始します。

## カメラ付きでテレオペする

カメラの種類は原本の [Cameras](https://huggingface.co/docs/lerobot/cameras) を見てください。SO-101 では OpenCV の USB カメラがよく使われます。解像度は 640×480、30fps が無難です。

`rerun` で映像と関節位置を見ながらテレオペする例:

```bash
lerobot-teleoperate \
    --robot.type=so101_follower \
    --robot.port=/dev/ttyACM0 \
    --robot.id=my_follower_arm \
    --robot.cameras="{front: {type: opencv, index_or_path: 0, width: 640, height: 480, fps: 30}}" \
    --teleop.type=so101_leader \
    --teleop.port=/dev/ttyACM1 \
    --teleop.id=my_leader_arm \
    --display_data=true
```

`index_or_path` はカメラ番号です。手首と真上の 2 台なら `wrist` と `top` のように名前を付け、0 と 1 を割り当てます。マウントの話は [オプション部品]({{ '/optional/' | relative_url }}) にあります。

## データセットを記録する

テレオペに慣れたら、最初のデータセットを取ります。Hugging Face Hub に上げる場合は、書き込み権限のあるトークンでログインします。トークンは [設定画面](https://huggingface.co/settings/tokens) で作れます。

```bash
hf auth login --token ${HUGGINGFACE_TOKEN} --add-to-git-credential
HF_USER=$(NO_COLOR=1 hf auth whoami | awk -F': *' 'NR==1 {print $2}')
echo $HF_USER
```

5 エピソードを記録して Hub に上げる例:

```bash
lerobot-record \
    --robot.type=so101_follower \
    --robot.port=/dev/ttyACM0 \
    --robot.id=my_awesome_follower_arm \
    --robot.cameras="{ front: {type: opencv, index_or_path: 0, width: 640, height: 480, fps: 30}}" \
    --teleop.type=so101_leader \
    --teleop.port=/dev/ttyACM1 \
    --teleop.id=my_awesome_leader_arm \
    --display_data=true \
    --dataset.repo_id=${HF_USER}/record-test \
    --dataset.num_episodes=5 \
    --dataset.single_task="黒いキューブをつかむ" \
    --dataset.streaming_encoding=true \
    --dataset.encoder_threads=2
```

ローカル保存先は `~/.cache/huggingface/lerobot/{repo-id}` です。記録後、データセットは Hugging Face のページ（例: `https://huggingface.co/datasets/${HF_USER}/so101_test`）に上がります。Hub に上げないときは `--dataset.push_to_hub=False` です。

### 記録中のキーボード

| キー | 動作 |
| --- | --- |
| 右矢印 または `n` | 今のエピソード / リセットを早めに終えて次へ |
| 左矢印 または `r` | 今のエピソードを破棄して撮り直し |
| Escape または `q` | セッションを止め、動画をエンコードし、アップロード |

これらの操作キーは X11 / Wayland / ヘッドレス SSH でも、対話的な端末から起動してフォーカスがあれば使えます。キーボードでロボット自体を動かすテレオペは別で、X11、Windows、またはアクセシビリティ権限のある macOS が必要です。

途中から足すときは `--resume=true` です。このとき `--dataset.num_episodes` は **追加する本数** で、合計ではありません。`--dataset.root` にローカルパスも必要です。最初からやり直すときはデータセットのディレクトリを手動で消します。

よく使う時間のパラメータ:

- `--dataset.episode_time_s=60` … 1 エピソードの長さ（既定 60 秒）
- `--dataset.reset_time_s=60` … エピソード間のリセット時間
- `--dataset.num_episodes=50` … 取る本数（既定 50）

### データの取り方

最初の課題は、物の位置を変えながらつかんで箱に入れる、が扱いやすいです。目安は **50 エピソード以上**、位置ごとに 10 本。カメラは固定し、つかみ方を揃え、対象が映像に入っていること。カメラ映像だけ見て自分でも作業できるか、が目安です。

安定してつかめるようになってから、位置・つかみ方・カメラ位置のばらつきを足していきます。最初から変化を増やしすぎると学習が苦しくなります。詳細は公式の [What makes a good dataset](https://huggingface.co/blog/lerobot-datasets#what-makes-a-good-dataset) です。

オンライン可視化は [visualize_dataset](https://huggingface.co/spaces/lerobot/visualize_dataset) に repo id を貼ります。

```bash
echo ${HF_USER}/so101_test
```

## エピソードを再生する

記録した動きをロボットに再生し、繰り返し精度を見ます。

```bash
lerobot-replay \
    --robot.type=so101_follower \
    --robot.port=/dev/ttyACM0 \
    --robot.id=my_awesome_follower_arm \
    --dataset.repo_id=${HF_USER}/record-test \
    --dataset.episode=0
```

## ポリシーを学習する

```bash
lerobot-train \
  --dataset.repo_id=${HF_USER}/so101_test \
  --policy.type=act \
  --output_dir=outputs/train/act_so101_test \
  --job_name=act_so101_test \
  --policy.device=cuda \
  --wandb.enable=true \
  --policy.repo_id=${HF_USER}/my_policy
```

要点:

1. `--dataset.repo_id` が学習データ
2. `--policy.type=act` が ACT。モーター数とカメラ枚数はデータセットから合わせる
3. GPU が NVIDIA なら `cuda`、Apple Silicon なら `mps`
4. `--wandb.enable=true` は任意。使うなら先に `wandb login`

数時間かかることが多いです。チェックポイントは `outputs/train/act_so101_test/checkpoints` に出ます。

続きから学習する例:

```bash
lerobot-train \
  --config_path=outputs/train/act_so101_test/checkpoints/last/pretrained_model/train_config.json \
  --resume=true
```

Hub に上げないなら `--policy.push_to_hub=false`。手元に強い GPU が無いときは、公式の [ACT training notebook](https://huggingface.co/docs/lerobot/notebooks#training-act) や [Hugging Face Jobs](https://huggingface.co/docs/hub/jobs)（`--job.target=a10g-small` など）があります。

## 推論して評価する

学習したポリシーを実機に載せるには `lerobot-rollout` です。`--strategy.type=base` は記録なしの自律実行、`sentry` は評価データを取りながら回します。

```bash
lerobot-rollout \
  --strategy.type=base \
  --policy.path=${HF_USER}/my_policy \
  --robot.type=so101_follower \
  --robot.port=/dev/ttyACM0 \
  --robot.cameras="{ front: {type: opencv, index_or_path: 0, width: 640, height: 480, fps: 30}}" \
  --task="黒いキューブを透明な箱に入れる" \
  --duration=60
```

カメラの名前と解像度は、学習データと揃えてください。Pi0 や SmolVLA など遅い VLA には `--inference.type=rtc` があります。

詰まったら [困ったとき]({{ '/troubleshooting/' | relative_url }}) と [Discord](https://discord.com/invite/s3KuuzsPFb) を見てください。
