# SO-100/101 用オーバーヘッドカメラ（32x32 カメラモジュール）取り付けガイド
<img height="200" src="../../media/overhead_cam_32x32_module.png" />
<img height="400" src="../../media/overhead_cam_two_followers.png" />
<img height="400" src="../../media/overhead_cam_one_follower.png" />

## 概要
このガイドでは、**32x32 カメラモジュール** と 3D プリントした **アームベース** および **カメラマウント** を使い、SO-100/101 に **オーバーヘッドカメラ** を取り付ける手順を説明します。

## 関連設計
* [Webカメラ版オーバーヘッドカメラ取り付けガイド](../Overhead_Cam_Mount_Webcam/README.md)

## 設計の狙い

1. カメラ位置とアーム間隔（双腕）を標準化し、SO-100 利用者間でデータを揃えやすくする。
2. 操作空間全体を真上から見られるようにする。
3. フォロワー 1 本でも、2 本の双腕（バイマニュアル）でも使えるようにする。

## 必要な部品
- **カメラモジュール**（1）— 32mm × 32mm。[検証済みの推奨モデル](https://www.amazon.com/dp/B0CLRJZG8D) がありますが、同サイズなら他でも使えることが多いです。
- **3D プリント部品**
    - [Arm Base](stl/arm_base.stl)（フォロワーアーム 1 本につき 1）
    - [Camera Mount Bottom](stl/cam_mount_bottom.stl)（1）
    - [Camera Mount Middle](stl/cam_mount_middle.stl)（1）
    - [Camera Mount Top](stl/cam_mount_top.stl)（1）
- **M2 ネジ**（16）— Feetech サーボに付属する小さい方のネジです。

<img height="200" alt="カメラモジュール例" src="https://github.com/user-attachments/assets/18099e1d-754c-4877-871f-9113a0dff062" />

## 組み立て手順

### 手順 1: **カメラモジュール** を **Mount Top** に取り付ける

1. **カメラモジュール** のレンズを **Camera Mount Top** の穴に通す。
</br><img height="250" src="../../media/overhead_cam_step1a.jpg" />

2. ネジ 4 本で **カメラモジュール** を **Mount Top** に固定する。
</br><img height="250" src="../../media/overhead_cam_step1b.jpg" />

### 手順 2: **Mount Middle** を **Mount Top** に取り付ける

1. **Mount Middle** を **Mount Top** に押し込む。
2. ネジ 4 本で固定する。
</br><img height="250" src="../../media/overhead_cam_step2.jpg" />

### 手順 3: **Mount Bottom** を **Mount Middle** に取り付ける

1. **Mount Bottom** を **Mount Middle** に押し込む。
2. ネジ 4 本で固定する。
</br><img height="250" src="../../media/overhead_cam_step3.jpg" />

### 手順 4: **Arm Base** を **Mount Bottom** に取り付ける
<img height="250" src="https://github.com/user-attachments/assets/732977ac-dd4a-4289-9d9c-8752c0369ff0"/></br>
1. **Arm Base** を **Mount Bottom** 側面のジョイントに押し込む。（フォロワーが 2 本なら繰り返す）
### 手順 5: **フォロワーアーム** を **Arm Base** に取り付ける
<img height="250" src="https://github.com/user-attachments/assets/24b4c0ce-e62b-4fd6-963c-09448e7ae6f9" /></br>
1. **フォロワーアーム** の底面を **Arm Base** の上面に合わせる。（フォロワーが 2 本なら繰り返す）
2. クランプでフォロワーを押さえている場合は、これまでと同じ締め方でカメラマウントも一緒に固定できます。

### 手順 6: ソフトウェアを設定する
1. ソフトウェアにオーバーヘッドカメラを追加し、解像度と FPS を設定する。
- **よく使う設定**:
    - FPS: 30
    - 解像度: 640 × 480。作業空間が広い場合は 1280 × 720。
2. 取り付けたカメラの映像を確認する（Mac なら *QuickTime* → *新規ムービー収録* でも見られます）。アームの作業空間が見えるはずです。もっと広く見たい場合は画面解像度を広げてください。

<img height="300" alt="映像例 1" src="https://github.com/user-attachments/assets/a0aded4e-6abf-4d19-a514-6d4be90ebe1b" />
<img height="300" alt="映像例 2" src="https://github.com/user-attachments/assets/d33287bd-0263-4a03-b7d9-54e360ef5a36" /></br>

### 手順 7:（任意）グリッパーカメラを追加する
<img height="250" src="https://github.com/user-attachments/assets/8e8fbf60-f62e-4d8c-8451-3ca5a864497c"/></br>
1. 学習データを良くするには、このマウントと合わせて設計された [**グリッパーカメラ**](../Wrist_Cam_Mount_32x32_UVC_Module) も追加してください。

## 謝辞

- Conor McGartoll
- Philip Fung
