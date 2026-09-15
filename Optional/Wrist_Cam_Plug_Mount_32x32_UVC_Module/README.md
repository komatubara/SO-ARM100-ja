# SO-100 用プラグ式手首カメラ（MF）取り付けガイド

<img height="300" src="https://github.com/user-attachments/assets/139be1c3-d446-4304-b0f4-c90a996789d6" />
<img height="300" src="https://github.com/user-attachments/assets/6c2f0f47-9663-4224-ac4e-220d1d71c162" />

## 概要
このガイドでは、**カメラモジュール** と 3D プリントした **プラグイン式カメラアダプタ** を使い、SO-100 に **手首カメラ**（別設計の "McGartoll-Fung" 版）を取り付ける手順を説明します。

[Wrist Camera (MF) UVC Module](../Wrist_Cam_Mount_32x32_UVC_Module/) の派生です。

## メイン設計との比較
#### 利点:
- 小さい
- 部品が少ない
- カメラ取り付けに追加のネジ／金具が不要
- 既存部品の取り外し／置き換えが不要
- 着脱が簡単

#### 欠点:
- 新しいカメラへの合わせ込みは必要

## 必要な部品
### ハードウェア:
- **USB カメラモジュール**（1）— [推奨モデル](https://www.amazon.com/innomaker-Computer-Raspberry-Support-Windows/dp/B0CNCSFQC1/ref=pd_lpo_d_sccl_3/132-7372155-9780230?pd_rd_w=eYz4L&content-id=amzn1.sym.4c8c52db-06f8-4e42-8e56-912796f2ea6c&pf_rd_p=4c8c52db-06f8-4e42-8e56-912796f2ea6c&pf_rd_r=XC3EXZRSSXKDB1G0Z5D7&pd_rd_wg=1wTpn&pd_rd_r=932b1976-9ac7-4cef-9774-f0f9c3acb804&pd_rd_i=B0CNCSFQC1&psc=1)。32mm × 32mm、最低 720p / 30fps の USB カメラモジュールなら他でも使えることが多いです
- [3D プリントしたプラグイン式カメラ取り付け部品](stl/SO-ARM100_Plug_camera.stl)（1）
   - STL の向きのままツリーサポートで印刷することを推奨。ぐらつきを防ぐためインフィル 40% が目安です
- **M2 ネジ**（8）— Feetech サーボに付属する小さい方のネジです。

<img height="200" alt="カメラモジュール例" src="https://github.com/user-attachments/assets/18099e1d-754c-4877-871f-9113a0dff062" />

## 組み立て手順
### 手順 1: 新しいカメラモジュールをグリッパーに差し込む

2. **プラグイン式カメラ取り付け部品** を 3D プリントする。

3. **プラグイン式カメラ取り付け部品** を取り付ける。
    1. 穴は [グリッパーの穴](../../STEP/Follower_specific/Moving_Jaw_08d%20v1.step) に合わせます。

4. M2 ネジで固定する。

### 手順 2: カメラを取り付ける
1. **カメラモジュール** を取り出す。
2. **カメラモジュール** の 4 穴を取り付け部品に合わせ、**M2 ネジ** 4 本で固定する。

<img height="300" src="https://github.com/user-attachments/assets/ea5af652-9311-44c7-8ae8-525f42cb4703" />

### 手順 3: ソフトウェア設定とフォーカス調整
1. ソフトウェアで解像度と FPS を設定する。
- **注意**: カメラの最大解像度が高くても、解像度は *640 × 480*、FPS は *30* が無難です。多くのモデルは低解像度で学習し、高すぎるとデータが膨らむだけです。
2. アームの電源を入れ、取り付けたカメラの映像を確認する（Mac なら *QuickTime* → *新規ムービー収録* でも見られます）。
- **注意**: フォーカスは手動で、最初はかなりボケて見えます。映像がはっきりするまでレンズを時計回り／反時計回りに回して調整してください。
