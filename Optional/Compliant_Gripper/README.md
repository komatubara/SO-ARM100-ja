# SO-101 アーム用コンプライアントグリッパーガイド

<img src="https://github.com/user-attachments/assets/26de0b8c-8bd6-4651-867f-1358532e2cc6" width="500">

コンプライアントグリッパーは、元の剛体グリッパーを柔軟材料（TPU）で印刷する改造です。内部リブ付きの中空構造で、つかむ対象の形に沿ってたわみ、接触力を下げます。形が難しい物や壊れやすい物（果物など）向きで、安全に扱うために必要な制御精度も下がります。

## 印刷手順

デモ用グリッパーは、Bambu Lab プリンタでショア硬度 95A の熱可塑性ポリウレタン（TPU）フィラメントを使い、インフィル 20% とサポート生成で印刷しました。印刷後、サポートはニッパーで手作業で外しています。

TPU のような柔軟フィラメントに対応していないプリンタもあります。ヘッドの換装などが必要な機種もあります。TPU は印刷時間が長くなりやすく、サポートが取りにくいため後処理も増えます。

## 取り付け手順（SO-101）

コンプライアントグリッパーでは、ロボットの組み立て手順や取り付け方法を変える必要はありません。外形は元のグリッパーと同じで、一部の穴をなくし、空洞とリブを足した程度です。

[Compliant_Moving_Jaw_SO101.stl](stl/Compliant_Moving_Jaw_SO101.stl) と [Compliant_Wrist_Roll_Follower_SO101.stl](stl/Compliant_Wrist_Roll_Follower_SO101.stl) を TPU 95A で印刷し、いつもどおり取り付けてください。

## 補足

この設計は、2025 年 6 月の Hugging Face LeRobot Hackathon で、メンフィス（テネシー州）の Zach Tabor と Caitlin Freeman が作りました。Festo のコンプライアントグリッパーで知られる Fin Ray Effect® にゆるく着想を得ています。
