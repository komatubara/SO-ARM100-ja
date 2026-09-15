# SO-100/101 用オーバーヘッドカメラ（Webカメラ）取り付けガイド
<img height="200" alt="オーバーヘッド Webカメラ" src="../../media/overhead_cam_webcam.jpg" />
<img height="400" alt="組み立て例" src="https://github.com/user-attachments/assets/a652e133-8672-448d-baa0-bdd494a0a515" />
<img height="400" alt="俯瞰視点" src="https://github.com/user-attachments/assets/050387cb-b701-47ed-bfb9-dabd29689272" />
<img height="400" alt="作業空間" src="https://github.com/user-attachments/assets/519d884d-dcb6-42a4-bff4-927858672f8b" />

## 概要
このガイドでは、**Webカメラ** と 3D プリントした **アームベース** および **カメラマウント** を使い、SO-100 に **オーバーヘッドカメラ** を取り付ける手順を説明します。

## 関連設計
* [32x32 カメラモジュール版オーバーヘッドカメラ](../Overhead_Cam_Mount_32x32_UVC_Module/README.md)

## 設計の狙い

1. カメラ位置とアーム間隔（双腕）を標準化し、SO-100 利用者間でデータを揃えやすくする。
2. 操作空間全体を真上から見られるようにする。
3. フォロワー 1 本でも、2 本の双腕（バイマニュアル）でも使えるようにする。

## 必要な部品
- **Webカメラ**（1）— [推奨モデル](https://www.amazon.com/dp/B082X91MPP)
- **3D プリント部品**
    - [Arm Base](stl/arm_base.stl)（フォロワーアーム 1 本につき 1）
    - [Camera Mount Bottom](stl/cam_mount_bottom.stl)（1）
    - [Camera Mount Top](stl/cam_mount_top.stl)（1）
- **M2 ネジ**（8）— Feetech サーボに付属する小さい方のネジです。

<img height="200" alt="カメラモジュール例" src="https://github.com/user-attachments/assets/18099e1d-754c-4877-871f-9113a0dff062" />

## 組み立て手順
### 手順 1: **Webカメラ** の既存ベースを外す
<img height="250" src="https://github.com/user-attachments/assets/89226328-16bf-41e2-b2e2-260352597b61" /> </br>
**Webカメラ** を箱から出し、次を行います。
1. 関節の柔らかいプラスチックカバーを外す。
2. 関節のネジを外す。
3. カメラモジュールからベースを外す。

### 手順 2: **Webカメラ** を **Camera Mount Top** に取り付ける
<img height="250" src="https://github.com/user-attachments/assets/051ebe6b-9548-47a0-81f7-df60a1ea5fad" /> </br>

1. 丸い関節穴を合わせ、**Webカメラ** を **Camera Mount Top** に押し込む。
2. 六角穴に六角ボルトを入れ、反対側の穴から **M2 ネジ** を締める。
### 手順 3: **Camera Mount Top** を **Camera Mount Bottom** に取り付ける
<img height="250" src="https://github.com/user-attachments/assets/434e4423-bf8a-4a36-95fb-d3c4283381a9" />

1. **Camera Mount Top** 底面の直線ジョイントと、**Camera Mount Bottom** 上面を合わせて押し込む。
2. 直線ジョイントの 4 穴それぞれに **M2 ネジ** を締める。
### 手順 4: **Arm Base** を **Camera Mount Bottom** に取り付ける
<img height="250" src="https://github.com/user-attachments/assets/732977ac-dd4a-4289-9d9c-8752c0369ff0"/></br>
1. **Arm Base** を **Camera Mount Bottom** 側面のジョイントに押し込む。（フォロワーが 2 本なら繰り返す）
### 手順 5: **SO-100 フォロワーアーム** を **Arm Base** に取り付ける
<img height="250" src="https://github.com/user-attachments/assets/24b4c0ce-e62b-4fd6-963c-09448e7ae6f9" /></br>
1. **SO-100 フォロワーアーム** の底面を **Arm Base** の上面に合わせる。（フォロワーが 2 本なら繰り返す）
2. クランプでフォロワーを押さえている場合は、これまでと同じ締め方でカメラマウントも一緒に固定できます。

### 手順 6: ソフトウェアを設定する
1. ソフトウェアにオーバーヘッドカメラを追加し、解像度と FPS を設定する。
- **注意**: カメラの最大解像度／フレームレートが高くても、解像度は *640 × 480*、FPS は *30* が無難です。多くのモデルは低解像度で学習し、高すぎるとデータが膨らむだけです。このマウントは 640 × 480 の解像度と幅を前提に設計されています。
2. 取り付けたカメラの映像を確認する（Mac なら *QuickTime* → *新規ムービー収録* でも見られます）。アームの作業空間が見えるはずです。

<img height="300" alt="映像例 1" src="https://github.com/user-attachments/assets/a0aded4e-6abf-4d19-a514-6d4be90ebe1b" />
<img height="300" alt="映像例 2" src="https://github.com/user-attachments/assets/d33287bd-0263-4a03-b7d9-54e360ef5a36" /></br>

### 手順 7:（任意）グリッパーカメラを追加する
<img height="250" src="https://github.com/user-attachments/assets/8e8fbf60-f62e-4d8c-8451-3ca5a864497c"/></br>
1. 学習データを良くするには、このマウントと合わせて設計された [**グリッパーカメラ**](../Wrist_Cam_Mount_32x32_UVC_Module) も追加してください。

## 謝辞

- Conor Mc Gartoll
    - 設計と研究開発
- Philip Fung
    - 研究開発
