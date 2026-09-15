# SO100 / SO101 のシミュレーションモデル

このフォルダには **SO100** と **SO101** のシミュレーション用ファイルが入っています。

## SO100

- SO100 ロボット用の **URDF** が 1 ファイルあります。
- **URDF** の可視化には [rerun](https://www.rerun.io/) と [URDF visualizer プラグイン](https://github.com/rerun-io/rerun-loader-python-example-urdf#installing-the-plugin) が使えます。

<img src="../media/so100_urdf.png" alt="SO100" width="40%">

```bash
rerun Simulation/SO100/so100.urdf
```

## SO101

- シミュレーション用の **URDF** と **MJCF**（MuJoCo）の両方があります。
- **URDF** の可視化には [rerun](https://www.rerun.io/) と [URDF visualizer プラグイン](https://github.com/rerun-io/rerun-loader-python-example-urdf#installing-the-plugin) が使えます。

```bash
rerun Simulation/SO101/so101_new_calib.urdf
rerun Simulation/SO101/so101_old_calib.urdf
```

詳細:
  - **旧キャリブレーション** と **新キャリブレーション** の URDF の違い
  - CAD モデルから **MJCF** を生成した方法

👉 [`Simulation/SO101/README.md`](SO101/README.md) を参照してください。
