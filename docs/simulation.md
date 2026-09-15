---
title: シミュレーション
eyebrow: URDF / MuJoCo
lead: 実機の前にモデルを動かしたいとき用です。SO-100 は URDF、SO-101 は URDF と MuJoCo（MJCF）があります。
---

可視化の手軽な方法は [rerun](https://www.rerun.io/) と [URDF プラグイン](https://github.com/rerun-io/rerun-loader-python-example-urdf#installing-the-plugin) です。

```bash
rerun Simulation/SO100/so100.urdf
rerun Simulation/SO101/so101_new_calib.urdf
rerun Simulation/SO101/so101_old_calib.urdf
```

<img src="https://raw.githubusercontent.com/TheRobotStudio/SO-ARM100/main/media/so100_urdf.png" alt="SO100 の URDF" style="max-width: 360px;">

## モデルの出自（SO-101）

Onshape の CAD から [onshape-to-robot](https://github.com/Rhoban/onshape-to-robot) で書き出しています。メッシュは `package://...` ではなく相対パスです。ベースの衝突メッシュは、計画やシミュレーションで不具合が多かったため外してあります。

STS3215 のモーター特性は [Open Duck Mini](https://github.com/apirrone/Open_Duck_Mini) の値を基にしています。

## 新旧キャリブレーション

`scene.xml` が読み込むファイルで切り替わります。

| 種類 | 仮想ゼロの置き方 | ファイル |
| --- | --- | --- |
| 新（デフォルト） | 各関節レンジの中央 | `so101_new_calib.xml` |
| 旧 | 水平に真っすぐ伸びた姿勢 | `so101_old_calib.xml` |

実機の LeRobot 校正（可動範囲をスイープする方式）に近いのは、中央をゼロにする新の方です。

## グリッパーの食い違い

LeRobot 上のグリッパーは直動で、`0` が閉、`100` が開です。この対応は **まだ URDF / MJCF に入っていません**。シミュレータと実機でグリッパー指令の意味が違う、という点だけ先に知っておくと混乱が減ります。
