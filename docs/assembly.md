---
title: SO-101 の組み立て
eyebrow: Hugging Face チュートリアル
lead: Hugging Face 公式の SO-101 ガイドを、動画つきで日本語にしたものです。モーターの ID 設定から関節ごとの組み方、校正まで、このページが本編です。
---

<p class="source-note">非公式訳です。原本は <a href="https://huggingface.co/docs/lerobot/so101">huggingface.co/docs/lerobot/so101</a>。手順が変わっているときは原本を優先してください。</p>

<img src="https://huggingface.co/datasets/huggingface/documentation-images/resolve/main/lerobot/SO101_Follower.webp" alt="SO-101 フォロワー" style="width:48%;border-radius:12px;">
<img src="https://huggingface.co/datasets/huggingface/documentation-images/resolve/main/lerobot/SO101_Leader.webp" alt="SO-101 リーダー" style="width:48%;border-radius:12px;">

以下は、Hugging Face がフラッグシップとしている **SO-101** の組み立て手順です。

## 部品を揃える

部品表と 3D プリントの説明は、このリポジトリの [README](https://github.com/TheRobotStudio/SO-ARM100)（日本語は [部品]({{ '/parts/' | relative_url }}) と [3Dプリント]({{ '/printing/' | relative_url }})）にあります。初めて印刷する場合や、プリンタを持っていない場合の案内もそこにあります。

## LeRobot を入れる

インストール手順は [LeRobot 導入]({{ '/software/' | relative_url }})、原本は [Installation Guide](https://huggingface.co/docs/lerobot/installation) です。

それに加えて、Feetech SDK が必要です。

```bash
pip install -e ".[feetech]"
```

## 組み立ての全体像

フォロワーアームは **STS3215、ギア比 1/345 が 6 個** です。リーダーは、自重を支えつつ手で動かしやすいよう、関節ごとにギア比が違います。

| リーダーの軸 | モーター | ギア比 |
| --- | :---: | :---: |
| 土台 / Shoulder Pan | 1 | 1 / 191 |
| 肩の上げ下げ / Shoulder Lift | 2 | 1 / 345 |
| 肘 / Elbow Flex | 3 | 1 / 191 |
| 手首曲げ / Wrist Flex | 4 | 1 / 147 |
| 手首回転 / Wrist Roll | 5 | 1 / 147 |
| グリッパー | 6 | 1 / 147 |

**先にモーターへ ID を振り、それから筐体に組みます。** ID 設定のときは、ボードにモーターを **1 個だけ** つなぎます。箱を開けたばかりなら、先に [サーボの準備]({{ '/servos/' | relative_url }}) を読んでください。コネクタ、電源、ジャンパ、出荷時 ID の話があります。

## モーターの設定

### 1. 各アームの USB ポートを探す

バスサーボ用アダプタを USB と電源に繋ぎ、次を実行します。指示が出たら、調べたい方のケーブルを抜きます。

```bash
lerobot-find-port
```

macOS の例:

```text
Finding all available ports for the MotorBus.
['/dev/tty.usbmodem575E0032081', '/dev/tty.usbmodem575E0031751']
Remove the USB cable from your MotorsBus and press Enter when done.

[...該当するリーダーまたはフォロワーの USB を抜いて Enter...]

The port of this MotorsBus is /dev/tty.usbmodem575E0032081
Reconnect the USB cable.
```

この例では、見つかったポートは `/dev/tty.usbmodem575E0032081` です。

Linux では、次で USB ポートの権限を付ける必要があることがあります。

```bash
sudo chmod 666 /dev/ttyACM0
sudo chmod 666 /dev/ttyACM1
```

Linux の例:

```text
Finding all available ports for the MotorBus.
['/dev/ttyACM0', '/dev/ttyACM1']
Remove the usb cable from your MotorsBus and press Enter when done.

[...該当するリーダーまたはフォロワーの USB を抜いて Enter...]

The port of this MotorsBus is /dev/ttyACM1
Reconnect the USB cable.
```

この例では `/dev/ttyACM1` です。

### 2. モーター ID とボーレートを書く

バス上の各モーターは、一意の ID で識別されます。新品はだいたい ID が `1` です。コントローラと通信するには、モーターごとに違う ID が必要です。通信速度はボーレートで決まり、コントローラと全モーターで同じ値に揃えます。

そのため、**モーターを 1 個ずつ** コントローラに繋いで設定します。値は EEPROM（電源を切っても残るメモリ）に書くので、基本は一度だけです。

別のロボットから流用したモーターも、ID とボーレートが合っていないことが多いので、この手順が必要です。

公式の手順動画:

<video controls playsinline>
  <source src="https://huggingface.co/datasets/huggingface/documentation-images/resolve/main/lerobot/setup_motors_so101_2.mp4" type="video/mp4">
</video>

#### フォロワー

PC からの USB と電源を、フォロワー側の制御ボードに繋ぎます。前の手順で分かったポートを使い、次を実行します。`id` はアームの名前です。

```bash
lerobot-setup-motors \
    --robot.type=so101_follower \
    --robot.port=/dev/tty.usbmodem585A0076841
```

ポートは自分の環境の値に置き換えてください。Python でも同じことができます。

```python
from lerobot.robots.so_follower import SO101Follower, SO101FollowerConfig

config = SO101FollowerConfig(
    port="/dev/tty.usbmodem585A0076841",
    id="my_awesome_follower_arm",
)
follower = SO101Follower(config)
follower.setup_motors()
```

次の指示が出ます。

```text
Connect the controller board to the 'gripper' motor only and press enter.
```

指示どおり、**グリッパーのモーターだけ** をボードに繋ぎます。デイジーチェーン（モーター同士の直列接続）はまだしません。`Enter` を押すと、そのモーターの ID とボーレートが自動で書かれます。

ここでエラーになるときは、次を確認します。

- 電源
- PC と制御ボードの USB
- ボードからモーターへの 3 ピンケーブル
- Waveshare ボードなら、ジャンパ 2 つが **B チャネル（USB）** 側か

成功すると次のように出ます。

```text
'gripper' motor id set to 6
```

続けて:

```text
Connect the controller board to the 'wrist_roll' motor only and press enter.
```

ボード側の 3 ピンは外して構いません。グリッパー側のコネクタはそのままで大丈夫です。別の 3 ピンケーブルで **wrist_roll だけ** をボードに繋ぎます。前と同じく、繋がっているモーターは 1 個だけにしてください。

指示どおり、残りのモーターでも繰り返します。

<div class="callout">
  <strong>TIP。</strong> Enter を押す前に配線を見てください。ボードを動かしていると、電源プラグが抜けやすいです。
</div>

スクリプトが終われば、モーターは使える状態です。ここからモーター同士を 3 ピンで数珠つなぎし、最初のモーター（`shoulder pan`、ID=1）から制御ボードへ戻します。ボードはアームのベースに取り付けられます。

#### リーダー

リーダーも同じ手順です。

```bash
lerobot-setup-motors \
    --teleop.type=so101_leader \
    --teleop.port=/dev/tty.usbmodem575E0031751
```

```python
from lerobot.teleoperators.so_leader import SO101Leader, SO101LeaderConfig

config = SO101LeaderConfig(
    port="/dev/tty.usbmodem585A0076841",
    id="my_awesome_leader_arm",
)
leader = SO101Leader(config)
leader.setup_motors()
```

## 印刷部品の下ごしらえ

3D プリント部品からサポートをすべて外します。小さいドライバーをサポートの下に入れて剥がすのが簡単です。

モーターを置いたら、組み立てを進める前に 3 ピンケーブルを 1 本差しておくことを公式は勧めています。後から奥へ手が入らなくなりやすいためです。

## 関節 1（土台）

- モーターホーンを上下に付ける。上のホーンは M3×6mm で固定。下のホーンにネジは不要
- 最初のモーターをベースへ入れる
- いちばん小さいネジ（M2×6mm）を 4 本。上から 2、下から 2
- 最初のモーターホルダーを被せ、左右それぞれ M2×6mm を 1 本
- ショルダー部品を取り付ける
- ショルダーを上から M3×6mm を 4 本、下から M3×6mm を 4 本で締める
- ショルダー側のモーターホルダーを追加する

<video controls playsinline>
  <source src="https://huggingface.co/datasets/huggingface/documentation-images/resolve/main/lerobot/Joint1_v2.mp4" type="video/mp4">
</video>

## 関節 2（上腕）

- ホーンは関節 1 と同じ。上だけ M3×6mm
- 2 番モーターを上から滑り込ませる
- M2×6mm を 4 本で固定
- 上腕を、左右それぞれ M3×6mm を 4 本で付ける

<video controls playsinline>
  <source src="https://huggingface.co/datasets/huggingface/documentation-images/resolve/main/lerobot/Joint2_v2.mp4" type="video/mp4">
</video>

## 関節 3（前腕 / 肘）

- ホーンは同様
- モーター 3 を入れ、M2×6mm を 4 本
- 前腕をモーター 3 へ、左右それぞれ M3×6mm を 4 本

<video controls playsinline>
  <source src="https://huggingface.co/datasets/huggingface/documentation-images/resolve/main/lerobot/Joint3_v2.mp4" type="video/mp4">
</video>

## 関節 4（手首曲げ）

- ホーンは同様
- モーターホルダー 4 を先に被せる
- モーター 4 を滑り込ませる
- M2×6mm を 4 本で固定

<video controls playsinline>
  <source src="https://huggingface.co/datasets/huggingface/documentation-images/resolve/main/lerobot/Joint4_v2.mp4" type="video/mp4">
</video>

## 関節 5（手首回転）

- モーター 5 を手首ホルダーへ入れ、正面の M2×6mm を 2 本で固定
- 手首モーターのホーンは **1 枚だけ**。M3×6mm のホーンネジで固定
- 手首をモーター 4 へ、両側それぞれ M3×6mm を 4 本

<video controls playsinline>
  <source src="https://huggingface.co/datasets/huggingface/documentation-images/resolve/main/lerobot/Joint5_v2.mp4" type="video/mp4">
</video>

## グリッパー / ハンドル

### フォロワーのグリッパー

- グリッパーをモーター 5 へ。手首のホーンに M3×6mm を 4 本
- グリッパー用モーターを入れ、左右それぞれ M2×6mm を 2 本
- ホーンを上下に付ける。上だけ M3×6mm。下はネジなし
- クロー（爪）を付け、両側それぞれ M3×6mm を 4 本

<video controls playsinline>
  <source src="https://huggingface.co/datasets/huggingface/documentation-images/resolve/main/lerobot/Gripper_v2.mp4" type="video/mp4">
</video>

### リーダーのハンドル

- リーダー用ホルダーを手首へ載せ、M3×6mm を 4 本
- ハンドルをホルダーへ、M2×6mm を 1 本
- グリッパー用モーターを入れ、左右それぞれ M2×6mm を 2 本。ホーンは M3×6mm のホーンネジ
- トリガーを M3×6mm を 4 本で付ける

<video controls playsinline>
  <source src="https://huggingface.co/datasets/huggingface/documentation-images/resolve/main/lerobot/Leader_v2.mp4" type="video/mp4">
</video>

## キャリブレーション（校正）

リーダーとフォロワーが同じ姿勢のとき、同じ位置の数値になるようにします。ある個体で学習したニューラルネットワークを、別の個体でも使うために重要な手順です。

### フォロワー

```bash
lerobot-calibrate \
    --robot.type=so101_follower \
    --robot.port=/dev/tty.usbmodem58760431551 \
    --robot.id=my_awesome_follower_arm
```

`--robot.port` は自分のポート、`--robot.id` はアームの固有名に変えてください。

```python
from lerobot.robots.so_follower import SO101FollowerConfig, SO101Follower

config = SO101FollowerConfig(
    port="/dev/tty.usbmodem585A0076891",
    id="my_awesome_follower_arm",
)

follower = SO101Follower(config)
follower.connect(calibrate=False)
follower.calibrate()
follower.disconnect()
```

公式動画の流れは次のとおりです。

1. すべての関節を、可動範囲の **真ん中** 付近へ持っていく
2. Enter を押す
3. 各関節を、端から端まで動かす

<video controls playsinline>
  <source src="https://huggingface.co/datasets/huggingface/documentation-images/resolve/main/lerobot/calibrate_so101_2.mp4" type="video/mp4">
</video>

肘をハードストップにぶつけやすい、6 軸を同時に中点へ保てない、という場合は [WebUI の 3 点校正]({{ '/calibration/' | relative_url }}) も使えます。

### リーダー

同じことをリーダーでも行います。

```bash
lerobot-calibrate \
    --teleop.type=so101_leader \
    --teleop.port=/dev/tty.usbmodem58760431551 \
    --teleop.id=my_awesome_leader_arm
```

```python
from lerobot.teleoperators.so_leader import SO101LeaderConfig, SO101Leader

config = SO101LeaderConfig(
    port="/dev/tty.usbmodem58760431551",
    id="my_awesome_leader_arm",
)

leader = SO101Leader(config)
leader.connect(calibrate=False)
leader.calibrate()
leader.disconnect()
```

これで、作業を学習させる準備はできています。続きは [データ収集と学習]({{ '/train/' | relative_url }})（原本: [Getting started with real-world robots](https://huggingface.co/docs/lerobot/il_robots)）です。

質問や困ったことは [Discord](https://discord.com/invite/s3KuuzsPFb) でも聞けます。
