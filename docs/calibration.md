---
title: キャリブレーション
eyebrow: 校正
lead: リーダーとフォロワーが同じ姿勢のとき、同じ数値になるようにします。別の個体で学習したモデルを移すときも、この対応が揃っていることが前提です。
---

公式の標準手順と動画: [SO-101 の Calibrate 節](https://huggingface.co/docs/lerobot/so101)

## 標準の校正（LeRobot）

### フォロワー

```bash
lerobot-calibrate \
    --robot.type=so101_follower \
    --robot.port=/dev/ttyACM0 \
    --robot.id=my_awesome_follower_arm
```

`--robot.id` は個体名です。校正ファイルの名前に使われるので、アームごとに変えます。

流れ:

1. すべての関節を、可動範囲の **真ん中** 付近へ持っていく
2. Enter
3. 各関節を、当たるところまで両方へゆっくり動かす

### リーダー

```bash
lerobot-calibrate \
    --teleop.type=so101_leader \
    --teleop.port=/dev/ttyACM1 \
    --teleop.id=my_awesome_leader_arm
```

終わると、同じ作業を実機で記録する準備ができます。続きは公式の [Getting started with real-world robots](https://huggingface.co/docs/lerobot/il_robots) です。

## WebUI の 3 点校正

手で 6 軸を同時に中点へ保つ標準法は、関節あたり数十〜200 ティックずれたり、肘（モーター 3 / `elbow_flex`）をハードストップにぶつけたりしやすい、というのが WebUI ガイドの問題意識です。

リポジトリの `Software/WEBUI_CALIBRATION.md` にある Studio は次の方針です。

- 関節ごとに Min / Home / Max を別々に記録する
- 動かすのは今選んでいる 1 サーボだけ。他は位置保持
- トルク上限 30%（レジスタ 48 = 300）
- 50Hz のコサイン S カーブで急発進を抑える
- `follower.json` を履歴ごと消さずに更新する

起動例:

```bash
python pi_servo_studio.py
```

または（ガイド記載）:

```bash
lerobot-calibrate --robot.type=so101_follower --webui
```

ブラウザで `http://localhost:8086` を開きます。

各モーター（1〜6）について:

1. 関節名をクリックする
2. 物理的な最小まで動かして **Capture Min**
3. 収納／休息姿勢で **Capture Home**
4. 物理的な最大まで動かして **Capture Max**

最後に **Safe Test Home**（30% トルク）で動きを見てから **Save Calibration** します。

<img src="{{ '/assets/servo_studio_dashboard.png' | relative_url }}" alt="Servo Studio の画面例" style="border-radius: 12px; border: 1px solid #d7cbb8;">

半二重のシリアル（よくあるのは `/dev/ttyACM0`）では、コマンド前に UART バッファを空にしないと古い応答が混ざることがあります。Studio 側でフラッシュする、とガイドに書かれています。
