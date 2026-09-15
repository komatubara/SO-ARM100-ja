---
title: 3Dプリント
eyebrow: 製作
lead: SO-101 のフレームは FDM 向けに向きが揃えた STL になっています。まずゲージで寸法を確認してから本番を刷ると、サーボが入らない事故を減らせます。
---

<img src="https://raw.githubusercontent.com/TheRobotStudio/SO-ARM100/main/media/SO101_Follower.webp" alt="印刷して組み立てたフォロワー" style="max-width: 420px; border-radius: 12px;">

## 推奨設定（SO-101）

| 項目 | 値 |
| --- | --- |
| 材料 | PLA+ |
| ノズル / 積層 | 0.4mm / 0.2mm、または 0.6mm / 0.4mm |
| インフィル | 15% |
| サポート | 出す。ただし 45 度より緩い斜面は無視 |
| 横向きのネジ穴 | サポートを入れない |

実機例: Prusa MINI+、UP Plus 2、Ender 3、Bambu Lab A / P / X シリーズ。

ベッドは水平を取り、油分を落としてから刷ります。スティックのりはプリンタが推奨する場合だけ薄く。

## 精度確認（ゲージ）

`STL/Gauges` に 2 系統あります。

- サーボがある: `Gauge_0.STL` と `Gauge_tight_1.STL`
- レゴ 4×2 がある: `Lego_Size_Test_02_zero.STL` と `Lego_Size_Test_02_minuspoint1.STL`

Gauge 0 のフィットは [公式が示す動画](https://youtu.be/dss8E3DG2rA) と同程度が目安です。ゆるすぎ・きつすぎならスケールやフローを見直してから本番に進みます。

## どのファイルを刷るか

リーダーとフォロワーは、それぞれ **1 トレイにまとまった STL** があります。Z 上向きです。

- ベッド 220×220mm（Ender など）  
  `STL/SO101/Follower/Ender_Follower_SO101.stl`  
  `STL/SO101/Leader/Ender_Leader_SO101.stl`
- ベッド 205×250mm（Prusa / Up）  
  `Prusa_Follower_SO101.stl` / `Prusa_Leader_SO101.stl`
- Bambu A1 mini 向けも `BambuLabA1mini_*` として別ファイルがあります

個別部品は `STL/SO101/Individual/` です。外注で 1 点ずつ上げるときはこちらを使います。

注意:

- `SO101 Assembly.stl` は参考用の全体モデルで、印刷しません
- マウントプレートは Waveshare 用か Seeed 用か、**基板に合わせて 1 種類だけ**
- 共通 9 点は両アームで使うので、2 本作るなら数量 2

印刷後はパテナイフでベッドから外し、サポートを取ります。四角い中空部品の圧入が硬いときは [マウントヘルパー](https://github.com/TheRobotStudio/SO-ARM100/tree/main/Optional/Mount_Helper) が使えます。

## プリンタが無いとき

原本の [3DPRINT.md](https://github.com/TheRobotStudio/SO-ARM100/blob/main/3DPRINT.md) に手順付きで載っています。

- **Craftcloud** — 個別 STL をアップロード。材料 PLA+、仕上げ Standard、インフィル 20%
- **PCBWay** — Ender 用の一体トレイ 2 ファイルを上げる。カスタム材料に `PLA+`、特記に `FDM, 20% infill`。原文の経験値ではリーダー + フォロワーで約 95 ドル前後（輸入税別）
- **Seeed** — プリント済みエンクロージャ単体も販売

日本国内の印刷サービスでも同じ PLA+ / インフィル目安で発注できます。ゲージを先に 1 個頼んで寸法を見るのも有効です。
