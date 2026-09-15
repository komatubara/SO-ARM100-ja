---
title: ソフトウェア
eyebrow: LeRobot
lead: ハードウェアが組めたら、Feetech バスサーボを LeRobot から見えるようにします。Linux では USB 権限、Windows / macOS ではポート名の確認が最初の関門です。
---

一次情報: [SO-101 ガイド](https://huggingface.co/docs/lerobot/so101) と [LeRobot のインストール](https://huggingface.co/docs/lerobot/installation)

## インストール

LeRobot 本体に加え、Feetech 用の追加依存が必要です。

```bash
pip install -e ".[feetech]"
```

仮想環境（conda や uv）に入れるのが無難です。CUDA が要るのは学習時で、モーター設定とデータ収集だけなら CPU でも進められます。

## USB ポートを特定する

制御ボードを USB と電源に繋ぎ、次を実行します。

```bash
lerobot-find-port
```

指示どおり、調べたい方のアームの USB を抜いて Enter します。残った／消えたポートがそのアームです。

例（macOS）:

```text
The port of this MotorsBus is /dev/tty.usbmodem575E0032081
```

例（Linux）:

```text
The port of this MotorsBus is /dev/ttyACM1
```

Linux では権限が足りないと開けません。

```bash
sudo chmod 666 /dev/ttyACM0
sudo chmod 666 /dev/ttyACM1
```

恒久化するなら `udev` ルールを追加します。接続のたびに chmod するのは忘れやすいです。

## モーター ID とボーレート

新品サーボの ID はだいたい `1` です。バス上で一意でないと通信できません。ボーレートもボードと全モーターで揃えます。EEPROM に書くので、基本は一度だけです。別ロボットから流用したモーターも、ここをやり直します。

**一度に 1 モーターだけ** をボードへ繋ぎます。デイジーチェーンしないこと。

### フォロワー

```bash
lerobot-setup-motors \
    --robot.type=so101_follower \
    --robot.port=/dev/ttyACM0
```

スクリプトが「gripper だけ繋げ」から順に指示します。公式の順番は先端（ID 6）から土台（ID 1）へ戻る形です。成功すると例えば次のように出ます。

```text
'gripper' motor id set to 6
```

次は `wrist_roll` だけ、と続きます。ケーブルはモーター側に残し、ボード側だけ差し替えても構いません。

### リーダー

```bash
lerobot-setup-motors \
    --teleop.type=so101_leader \
    --teleop.port=/dev/ttyACM1
```

全部終わったら、モーター同士を 3 ピンで数珠つなぎし、ID 1（shoulder pan）からボードへ戻します。

## うまくいかないとき

- 電源、USB、3 ピンの 3 本が実際に刺さっているか
- Waveshare ならジャンパが USB の `B` 側か
- 操作中に電源プラグが抜けていないか（公式も注意書きあり）

Windows での単体デバッグには [Feetech 公式ソフト](https://www.feetechrc.com/software.html)、Ubuntu には [FT_SCServo_Debug_Qt](https://github.com/Kotakku/FT_SCServo_Debug_Qt) もあります。LeRobot だけでも設定はできます。
