<div align="center">

   <h1>Standard Open SO-100 & SO-101 Arms</h1>
   <p><strong>非公式日本語ドキュメント</strong></p>
   <div style="display: flex; gap: 1rem; justify-content: center; align-items: center;" >
   <img
      src="media/SO101_Follower.webp?raw=true"
      alt="SO-101 フォロワーアーム"
      title="SO-101 フォロワーアーム"
      style="width: 40%;"
    />
   <img
      src="media/SO101_Leader.webp?raw=true"
      alt="SO-101 リーダーアーム"
      title="SO-101 リーダーアーム"
      style="width: 40%;"
    />
</div>

<h2>
    <p>自分で SO-101 ロボットを組み立てよう</p>
</h2>

</div>

> **これは非公式の日本語訳です。** 原本は [TheRobotStudio/SO-ARM100](https://github.com/TheRobotStudio/SO-ARM100)（[RobotStudio](https://www.therobotstudio.com) と [Hugging Face](https://huggingface.co/lerobot) の共同設計）です。英語原文は [README.en.md](README.en.md) を参照してください。
>
> **日本語解説サイト（GitHub Pages）:** [https://komatubara.github.io/SO-ARM100-ja/](https://komatubara.github.io/SO-ARM100-ja/)

SO‑101 は、もともと RobotStudio と Hugging Face が共同で設計した SO‑100 ロボットアームの次世代版です。配線が改善され、組み立てが簡単になり（ギアの取り外しが不要）、リーダーアーム用モーターも更新されています。

これらのアームは、オープンソースの 🤗 LeRobot ライブラリと組み合わせて使う前提で設計されています。ハードウェアとソフトウェアの両方について、[Discord](https://discord.gg/ggrqhPTsMe) コミュニティで協力しながら、エンドツーエンドのロボット AI をより身近にすることを目指しています。

### ドキュメント 📖
- SO‑101 の説明は、このページの続きを読んでください。
- 旧版の [SO‑100 ドキュメント](SO100.md) は非推奨です。
- 手順を追って読みたい場合は、[日本語解説サイト](https://komatubara.github.io/SO-ARM100-ja/) が便利です。

### SO‑101 を入手する
次の 2 通りがあります。
- **自分で組み立てる**
   - [部品表](#部品の調達) から部品を揃える。
   - 部品を 3D プリントする（またはプリント済み部品を注文する）。詳細は [部品のプリント](#部品のプリント)。
   - [組み立てガイド](https://huggingface.co/docs/lerobot/so101)（英語）に従う。日本語の要約は [解説サイトの組み立てページ](https://komatubara.github.io/SO-ARM100-ja/assembly/) を参照。
- **キットを買う**
   - [こちら](#キット) の販売元から、組み立て済みアームまたは部品キットを購入する。
   - 必要に応じて [組み立てガイド](https://huggingface.co/docs/lerobot/so101) も参照する。

### LeRobot 🤗 でのセットアップ
部品が揃ったら、LeRobot の [チュートリアル](https://huggingface.co/docs/lerobot/so101) に沿って SO-101 をセットアップできます。日本語の手順は [解説サイト](https://komatubara.github.io/SO-ARM100-ja/software/) にまとめています。

### オプションハードウェア 🔧
このリポジトリには、リーダー用のかさ上げベースや各種カメラマウントなど、拡張用のハードウェア設計も含まれています。[一覧はこちら](#オプションハードウェア)。


## キット

SO-100 / SO-101 用のキットは次の販売元で入手できます。

- RobotEd :switzerland: [スイス](https://roboted.ch/en/shop/so-101-robot-arm-kit)（**3D プリントフレームキット**、**電子部品キット**、**完成アームキット**）
- Robonine :earth_africa: [国際](https://robonine.com/)（**部品**キット）
- PartaBot :us: [米国](https://partabot.com)（**組み立て済み**、LeKiwi や Koch ロボットも販売）
- ForgeMotion Labs :us: [米国](https://forgemotionlabs.com/products) または [Amazon US](https://www.amazon.com/s?me=A3TE39P97BKL59)（**3D プリントフレームキット**、**電子部品キット**、**完成アームキット**）
- Seeed Studio :earth_africa: [国際](https://www.seeedstudio.com/SO-ARM100-Low-Cost-AI-Arm-Kit.html) / :cn: [中国](https://item.taobao.com/item.htm?id=878010637397&skuId=5915703371829&spm=a213gs.v2success.0.0.4cbf4831mkqWLn) / :jp: [秋月電子](https://akizukidenshi.com/catalog/g/g131169/) / [Aliexpress](https://www.aliexpress.com/item/3256808696884714.html?gatewayAdapt=4itemAdapt)（**3D プリントキット**）
- WowRobo :earth_africa: [国際](https://shop.wowrobo.com/products/so-arm101-diy-kit-assembled-version-1) / :cn: [中国](https://item.taobao.com/item.htm?ft=t&id=860171734711)（**組み立て済み**）
- RoboSEasy :kr: [韓国](https://smartstore.naver.com/roboseasy)
- NeoBot :cn: [中国](https://item.taobao.com/item.htm?ft=t&id=957685951340)
- Autodiscovery :eu: [EU](https://autodiscovery.eu/en/products/so-101-kit??utm_source=hf&utm_medium=shop&utm_content=web)

フォロワーアームのみのキット（リーダーなし）は [Phospho](https://robots.phospho.ai) でも入手できます。VR ヘッドセットを持っている場合に特に便利です。

日本から買う場合の目安は、**秋月電子の Seeed キット**と、下の部品表の **Buy JP** 列です。

## 部品の調達

このテレオペレーション構成では、フォロワーアームとリーダーアームの市販部品はほぼ同じです（モーターだけ異なります）。`LeRobot` ライブラリで使う定番の遠隔操作セットを作る場合は、下の「2 本アーム用部品」から購入してください。

現時点では US / EU / CN / JP のリンクのみです。他の国のリンクを見つけたら、Issue か PR で追加してもらえると助かります。価格や取り扱い商品は地域によって異なります。

> [!IMPORTANT]
> フォロワーアーム用の STS3215 モーターには 2 種類のサイズがあります。7.4V 版は 6V 時のストールトルクが 16.5kg·cm（5V 電源ではやや下がる見込み）です。12V 版はストールトルク 30kg·cm です。7.4V でも十分なことが多いですが、より強力なモーターが欲しければ 12V 版を [こちら](https://www.alibaba.com/product-detail/6PCS-12V-30KG-STS3215-High-Torque_1601216757543.html) から購入できます。その場合、5V ではなく 12V 5A 以上の電源も必要です。SO-101 のリーダーアームは常に 7.4V です。

#### 2 本アーム用部品（フォロワー + リーダー）:

| 部品 | 数量 | 単価 (US) | 購入 US | 単価 (EU) | 購入 EU | 単価 (RMB) | 購入 CN | 単価 (JPY) | 購入 JP |
| ------------------------------------------- | ------ | -------------- | --------------------------------------------------------------------------------------------------------- | -------------- | ------------------------------------------------------------------------------------------------- | --------------- | ------------------------------------------------------------------------------- | --------------- | ------------------------------------------------------------------------------- |
| STS3215 サーボ 7.4V、1/345 ギア (C001) **<sup>[2](#leaderbundle)</sup>  | 7     | $13.89            | [Alibaba](https://www.alibaba.com/product-detail/Top-Seller-Low-Cost-Feetech-STS3215_1600999461525.html)         | €12.2           | [Alibaba](https://www.alibaba.com/product-detail/Top-Seller-Low-Cost-Feetech-STS3215_1600999461525.html) | ￥97.72         | [TaoBao](https://item.taobao.com/item.htm?id=712179366565&skuId=5268252241438)  | ￥2,980         | [秋月電子](https://akizukidenshi.com/catalog/g/g116312/)  |
| STS3215 サーボ 7.4V、1/191 ギア (C044) **<sup>[2](#leaderbundle)</sup>   | 2     | $13.89            | [Alibaba](https://www.alibaba.com/product-detail/Feetech-STS3215-SO-ARM101-Servo-7_1601430747897.html?spm=a2747.product_manager.0.0.59a371d2W4e0SR)         | €12.2           | [Alibaba](https://www.alibaba.com/product-detail/Feetech-STS3215-SO-ARM101-Servo-7_1601430747897.html?spm=a2747.product_manager.0.0.59a371d2W4e0SR) | ￥97.72         | -  | ￥2,980         | [秋月電子](https://akizukidenshi.com/catalog/g/g131131/)  |
| STS3215 サーボ 7.4V、1/147 ギア (C046) **<sup>[2](#leaderbundle)</sup>    | 3     | $13.89            | [Alibaba](https://www.alibaba.com/product-detail/Feetech-STS3215-SO-ARM101-Servo-7_1601430760797.html?spm=a2747.product_manager.0.0.167371d25QeX3F)         | €12.2           | [Alibaba](https://www.alibaba.com/product-detail/Feetech-STS3215-SO-ARM101-Servo-7_1601430760797.html?spm=a2747.product_manager.0.0.167371d25QeX3F) | ￥97.72         | -  | ￥2,980         | [秋月電子](https://akizukidenshi.com/catalog/g/g131132/)  |
| モーター制御ボード                         | 2      | $10.6           | [Amazon](https://www.amazon.com/Waveshare-Integrates-Control-Circuit-Supports/dp/B0CTMM4LWK/)             | €11.4            | [Amazon](https://www.amazon.fr/-/en/dp/B0CJ6TP3TP/)                                               | ￥27            | [TaoBao](https://detail.tmall.com/item.htm?id=738817173460&skuId=5096283384143) | ￥980         | [秋月電子](https://akizukidenshi.com/catalog/g/g131227/)  |
| USB-C ケーブル 2 本セット                           | 1      | $7             | [Amazon](https://www.amazon.com/Charging-etguuds-Charger-Braided-Compatible/dp/B0B8NWLLW2/?th=1)          | €7             | [Amazon](https://www.amazon.fr/dp/B07BNF842T/)                                                    | ￥23.9\*2       | [TaoBao](https://detail.tmall.com/item.htm?id=44425281296&skuId=5611379016222)  | ￥1,498         | [Amazon](https://www.amazon.co.jp/dp/B0C3H9L6KZ)  |
| 電源    | 2      | $10            | [Amazon](https://www.amazon.com/Facmogu-Switching-Transformer-Compatible-5-5x2-1mm/dp/B087LY41PV/)        | €15.7            | [Amazon](https://www.amazon.fr/-/en/dp/B01HRR9GY4/)                                               | ￥22.31         | [TaoBao](https://item.taobao.com/item.htm?id=544824248494&skuId=4974994129990)  | ￥1,550         | [秋月電子](https://akizukidenshi.com/catalog/g/g106238/)  |
| テーブルクランプ 4 個セット                            | 1      | $9             | [Amazon](https://www.amazon.com/TAODAN-Trigger-Ratchet-Woodworking-Processes/dp/B0DJNXF8WH?rps=1&sr=1-18) | €9.7 | [Amazon](https://www.amazon.fr/Connex-COXT865210-Lot-Serre-joints-bricolage/dp/B00NA3T2CQ)      | ￥5.2*4 | [TaoBao](https://detail.tmall.com/item.htm?id=801399113134&skuId=5633627126649)                   | ￥2,200         | [Amazon](https://www.amazon.co.jp/dp/B0DJNXF8WH)  |
| ドライバーセット<sup>[1](#myfootnote1)</sup> | 1      | $6             | [Amazon](https://www.amazon.com/Precision-Phillips-Screwdriver-Electronics-Computer/dp/B0DB227RTH)        | €9            | [Amazon](https://www.amazon.fr/Vinabo-Magnétique-Electronique-Réparation-Informatique/dp/B0BNQBNFFJ)                                                    | ￥14.9          | [TaoBao](https://detail.tmall.com/item.htm?id=675684600845&skuId=4856851392176) | ￥500         | [Amazon](https://www.amazon.co.jp/dp/B01MDNJVMN)  |
| 合計                                       | ---    | $229.88           | ---                                                                                                       | €226.3           | ---                                                                                               | ￥1343.16       | ---                                                                             | ￥44,530         | ---                                                                             |

<a name="leaderbundle">2</a>: SO-101 リーダーアームに必要な **STS3215 サーボ 6 個すべて**  
（3 × 1/147 ギア (C046)、2 × 1/191 ギア (C044)、1 × 1/345 ギア (C001)）は、[Alibaba のセット](https://www.alibaba.com/product-detail/6PCS-7-4V-STS3215-Servos-for_1601428584027.html?spm=a2747.product_manager.0.0.757c2c3clU7uH3) でまとめて購入できます。

#### フォロワーアーム 1 本用部品:

| 部品 | 数量 | 単価 (US) | 購入 US | 単価 (EU) | 購入 EU | 単価 (RMB) | 購入 CN | 単価 (JPY) | 購入 JP |
| ------------------------------------------- | ------ | -------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- | -------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- | --------------- | ------------------------------------------------------------------------------- | --------------- | ------------------------------------------------------------------------------- |
| STS3215 サーボ 7.4V、1/345 ギア (C001)    | 6      | $13.89            | [Alibaba](https://www.alibaba.com/product-detail/Top-Seller-Low-Cost-Feetech-STS3215_1600999461525.html?spm=a2747.product_manager.0.0.11be71d2ARQb82) | €12.2            | [Alibaba](https://www.alibaba.com/product-detail/Top-Seller-Low-Cost-Feetech-STS3215_1600999461525.html?spm=a2747.product_manager.0.0.11be71d2ARQb82) | ￥97.72         | [TaoBao](https://item.taobao.com/item.htm?id=712179366565&skuId=5268252241438)  | ￥2,980         | [秋月電子](https://akizukidenshi.com/catalog/g/g116312/)  |
| モーター制御ボード                         | 1      | $10.6            | [Amazon](https://www.amazon.com/Waveshare-Integrates-Control-Circuit-Supports/dp/B0CTMM4LWK/)                                                         | €11.4            | [Amazon](https://www.amazon.fr/-/en/dp/B0CJ6TP3TP/)                                                                                                   | ￥27            | [TaoBao](https://detail.tmall.com/item.htm?id=738817173460&skuId=5096283384143) | ￥980         | [秋月電子](https://akizukidenshi.com/catalog/g/g131227/)  |
| USB-C ケーブル 2 本セット                           | 1      | $7             | [Amazon](https://www.amazon.com/Charging-etguuds-Charger-Braided-Compatible/dp/B0B8NWLLW2/?th=1)                                                      | €7             | [Amazon](https://www.amazon.fr/dp/B07BNF842T/)                                                                                                        | ￥23.9          | [TaoBao](https://detail.tmall.com/item.htm?id=44425281296&skuId=5611379016222)  | ￥1,498         | [Amazon](https://www.amazon.co.jp/dp/B0C3H9L6KZ)  |
| 電源    | 1      | $10            | [Amazon](https://www.amazon.com/Facmogu-Switching-Transformer-Compatible-5-5x2-1mm/dp/B087LY41PV/)                                                    | €15.7            | [Amazon](https://www.amazon.fr/-/en/dp/B01HRR9GY4/)                                                                                                   | ￥22.31         | [TaoBao](https://item.taobao.com/item.htm?id=544824248494&skuId=4974994129990)  | ￥1,550         | [秋月電子](https://akizukidenshi.com/catalog/g/g106238/)  |
| テーブルクランプ 2 個セット                            | 1      | $5             | [Amazon](https://www.amazon.com/Mr-Pen-Carpenter-Clamp-6inch/dp/B092L925J4/)                                                                          | €8             | [Amazon](https://www.amazon.fr/-/en/dp/B08HZ1QRBF/)                                                                                                   | ￥7.8           | [TaoBao](https://detail.tmall.com/item.htm?id=738636473238&skuId=5505939904942) | ￥2,200         | [Amazon](https://www.amazon.co.jp/dp/B0DJNXF8WH)  |
| ドライバーセット<sup>[1](#myfootnote1)</sup> | 1      | $6             | [Amazon](https://www.amazon.com/Precision-Phillips-Screwdriver-Electronics-Computer/dp/B0DB227RTH)                                                    | €9            | [Amazon](https://www.amazon.fr/Vinabo-Magnétique-Electronique-Réparation-Informatique/dp/B0BNQBNFFJ)                                                                                                        | ￥14.9          | [TaoBao](https://detail.tmall.com/item.htm?id=675684600845&skuId=4856851392176) | ￥500         | [Amazon](https://www.amazon.co.jp/dp/B01MDNJVMN)  |
| 合計                                       | ---    | $121.94           | ---                                                                                                                                                   | €124.3        | ---                                                                                                                                                   | ￥682.23        | ---                                                                             | ￥24,414        | ---                                                                             |

<a name="myfootnote1">1</a>: このドライバーセットそのものが必須ではありませんが、プラスドライバーの **#0** と **#1** があるとネジの取り付け・取り外しが格段に楽です。小型ドライバーセットに入っている標準サイズです。

## 部品のプリント

フォロワー／リーダーアームに必要な部品は、さまざまな 3D プリンタで印刷できます。以下の手順で、失敗しにくい印刷を目指してください。

### 手順 1: プリンタを選ぶ
同梱の STL は、多くの FDM プリンタでそのまま印刷できます。検証済みの推奨設定は次のとおりです（他の設定でも動く場合があります）。
   1. 材料: PLA+
   2. ノズル径と精度: ノズル 0.4mm / 積層 0.2mm、またはノズル 0.6mm / 積層 0.4mm
   3. インフィル密度: 15%
   4. 実機例: [Prusa MINI+](https://www.prusa3d.com/product/original-prusa-mini-semi-assembled-3d-printer-4/)、[UP Plus 2](https://shop.tiertime.com/product/tiertime-up-plus-2-3d-printer/)、[Creality Ender 3](https://www.amazon.com/Comgrow-Creality-Ender-Aluminum-220x220x250mm/dp/B07BR3F9N6/)、[Bambu Lab A/P/X シリーズ](https://bambulab.com)

### 手順 2: プリンタを準備する
   1. キャリブレーションとベッドレベリングが正しくできていることを、プリンタの手順に従って確認する。
   2. プリントベッドを清掃し、ホコリや油分を落とす。水などで洗った場合はよく乾かす。
   3. プリンタが推奨する場合は、スティックのりをベッドの印刷面に薄く均一に塗る。ダマやムラは避ける。
   4. フィラメントをプリンタの手順どおりに装填する。
   5. 印刷設定を上記の推奨に近づける（プリセットが複数ある場合は、いちばん近いものを選ぶ）。
   6. サポートは全体に出すが、水平面から 45 度より緩い斜面は無視する。
   7. 横向きのネジ穴にはサポートを入れない。

### 手順 3: プリンタの精度を確認する
   1. [Gauges](STL/Gauges) フォルダには 2 種類のゲージがあります。標準の 4x2 レゴブロック用と、STS3215 サーボ用です。
      1. STS3215 サーボがある場合は次を印刷:
         1. [Gauge Zero](STL/Gauges/Gauge_0.STL)
         2. [Gauge Tight](STL/Gauges/Gauge_tight_1.STL)
      2. 標準レゴブロックがある場合は次を印刷:
         1. [Gauge Zero](STL/Gauges/Lego_Size_Test_02_zero.STL)
         2. [Gauge -0.1](STL/Gauges/Lego_Size_Test_02_minuspoint1.STL)
   2. Gauge 0 を対象物（レゴまたはサーボ）に当てて確認する。フィット感は [この動画](https://youtu.be/dss8E3DG2rA) と同程度が目安です。
   3. フィットが適切なら手順 4 へ。そうでなければ設定を変えて再印刷するか、Issue を立ててください。

### 手順 4: 部品を印刷する
リーダーまたはフォロワーの部品は、**1 ファイルにまとめて** あり、Z 上向きでサポートが最小になる向きになっています。
   1. ベッドサイズ 220mm × 220mm（Ender など）の場合:
      - [Follower](STL/SO101/Follower/Ender_Follower_SO101.stl)
      - [Leader](STL/SO101/Leader/Ender_Leader_SO101.stl)
   2. ベッドサイズ 205mm × 250mm（Prusa / Up など）の場合:
      1. [Follower](STL/SO101/Follower/Prusa_Follower_SO101.stl)
      2. [Leader](STL/SO101/Leader/Prusa_Leader_SO101.stl)

個別ファイルの一覧:

<details>
<summary>個別部品ファイル</summary>

#### 共通部品

| 部品 | リンク |
|-------------------------------------|------------------------------------------------------------------|
| Base_motor_holder_SO101.stl         | [Base_motor_holder_SO101.stl](STL/SO101/Individual/Base_motor_holder_SO101.stl)       |
| Base_SO101.stl                      | [Base_SO101.stl](STL/SO101/Individual/Base_SO101.stl)                                 |
| Motor_holder_SO101_Base.stl         | [Motor_holder_SO101_Base.stl](STL/SO101/Individual/Motor_holder_SO101_Base.stl)       |
| Motor_holder_SO101_Wrist.stl        | [Motor_holder_SO101_Wrist.stl](STL/SO101/Individual/Motor_holder_SO101_Wrist.stl)     |
| Under_arm_SO101.stl                 | [Under_arm_SO101.stl](STL/SO101/Individual/Under_arm_SO101.stl)                       |
| Upper_arm_SO101.stl                 | [Upper_arm_SO101.stl](STL/SO101/Individual/Upper_arm_SO101.stl)                       |
| Rotation_Pitch_SO101.stl            | [Rotation_Pitch_SO101.stl](STL/SO101/Individual/Rotation_Pitch_SO101.stl)             |
| Wrist_Roll_Pitch_SO101.stl          | [Wrist_Roll_Pitch_SO101.stl](STL/SO101/Individual/Wrist_Roll_Pitch_SO101.stl)         |
| WaveShare_Mounting_Plate_SO101.stl  | [WaveShare_Mounting_Plate_SO101.stl](STL/SO101/Individual/WaveShare_Mounting_Plate_SO101.stl) |

#### リーダー専用部品

| 部品 | リンク |
|-----------------------|------------------------------------------|
| Handle_SO101.stl      | [Handle_SO101.stl](STL/SO101/Individual/Handle_SO101.stl)     |
| Trigger_SO101.stl     | [Trigger_SO101.stl](STL/SO101/Individual/Trigger_SO101.stl)   |
| Wrist_Roll_SO101.stl  | [Wrist_Roll_SO101.stl](STL/SO101/Individual/Wrist_Roll_SO101.stl) |

#### フォロワー専用部品

| 部品 | リンク |
|---------------------------------|--------------------------------------------------------------|
| Moving_Jaw_SO101.stl            | [Moving_Jaw_SO101.stl](STL/SO101/Individual/Moving_Jaw_SO101.stl)                 |
| Wrist_Roll_Follower_SO101.stl   | [Wrist_Roll_Follower_SO101.stl](STL/SO101/Individual/Wrist_Roll_Follower_SO101.stl) |
</details>

### 手順 5: サポートを外す
   1. 印刷が終わったら、パテナイフなどでベッドから部品を剥がす。
   2. サポート材を取り除く。

### 3D プリンタを持っていない場合
こちら: [印刷サービス](./3DPRINT.md)

## オプションハードウェア
SO‑100 / SO‑101 を次のアドオンで拡張できます。
<details>
<summary>アドオン一覧</summary>

#### 0. XLeRobot

日常用途向けの双腕モバイルロボット。SO101 アーム ×2、Lekiwi ベース ×1、Anker 300Wh バッテリー ×1、手首 RGB カメラ ×2、頭部デプスカメラ ×1（2 自由度ネック付き）。総額約 660 ドル。

<img width="1725" height="1140" alt="XLeRobot" src="https://github.com/user-attachments/assets/10819ef0-80a2-4cfe-be81-7daa8918cca1" />

[→ 完全なドキュメント](https://xlerobot.readthedocs.io/en/latest/index.html)（部品表、3D モデル、組み立て、シミュレーション、テレオペガイド）


#### 1. マウントヘルパー
組み立て時の位置合わせを楽にする治具です。

[→ README を見る](Optional/Mount_Helper/README.md)

<img src="media/mount_helper.png" alt="Mount Helper" width="150">

#### 2. オーバーヘッドカメラマウント

単腕・双腕（バイマニュアル）で真上からの視点を取るためのマウントです。
（SO100/101）

| Webカメラ | 32×32 カメラモジュール |
|:---------------------:|:-------------------:|
<img src="https://github.com/user-attachments/assets/a652e133-8672-448d-baa0-bdd494a0a515" height="200"> | <img src="media/overhead_cam_two_followers.png" height="200">
| [手順](Optional/Overhead_Cam_Mount_Webcam/README.md) | [手順](Optional/Overhead_Cam_Mount_32x32_UVC_Module/README.md)

#### 3. ベースマウント

| リーダー用かさ上げベース | 4040 アルミフレームマウント |
|:-------------------:|:---------------------------:|
<img src="media/Raised_Base.jpeg" height="150"> | <img src="media/4040_base_mount.jpg" height="150">
[STL をダウンロード](Optional/Raised_Base/Raised_Base_Extension.stl) | [手順](Optional/4040_Base_Mount/README.md)

#### 4. 触覚センサ（AnySkin）
グリッパーに触覚を追加できます。

[→ WOWROBO で探す](https://shop.wowrobo.com/products/enhanced-anyskin-premium-crafted-editionwowskin)

<img src="media/tactile_sensor_anyskin.png" alt="AnySkin Sensor" width="150">


#### 5. 手首カメラマウント

| 32×32 UVC 六角ナット（SO101） | 32×32 UVC 一体型（SO100/101） | 32×32 UVC プラグオン | RealSense D405 | RealSense D435/D435I | Webカメラ（Vinmooog） |
| --- | --- | --- | --- | --- | --- |
| <img src="media/UVC_cam_mount_so101.jpg" height="100"> | <img src="media/Wrist_Cam_Mount_32x32_UVC_module_1.jpg" height="100"> | <img src="media/UVC_cam_mount_plugin.jpg" height="100"> | <img src="media/d405_mount.jpg" height="100"> | <img src="media/d435_mount.jpg" height="100"> | <img src="media/cam_mount2.jpg" height="100"> |
| [手順](Optional/SO101_Wrist_Cam_Hex-Nut_Mount_32x32_UVC_Module) | [手順](Optional/Wrist_Cam_Mount_32x32_UVC_Module/README.md) | [手順](Optional/Wrist_Cam_Plug_Mount_32x32_UVC_Module) | [手順](Optional/Wrist_Cam_Mount_RealSense_D405) | [手順](Optional/Wrist_Cam_Mount_RealSense_D435) | [手順](Optional/Wrist_Cam_Mount_Vinmooog_Webcam) |



#### 6. コンプライアントグリッパー
TPU 95A などの柔軟フィラメントで印刷し、グリッパーに柔軟性を持たせます。

[→ README を見る](Optional/Compliant_Gripper/README.md)

<img src="https://github.com/user-attachments/assets/26de0b8c-8bd6-4651-867f-1358532e2cc6" width="150">

#### 7. コンプライアントグリッパー（新版）
指は TPU 95A、ベースは PLA で印刷します。
構造と把持（精度・力の両方）が改善されています。TPU の指はサポート不要です。M3 ネジが追加で 2 本必要。摩擦を上げたい場合は 3M のグリッパテープも使えます。
![新版コンプライアントグリッパー](https://github.com/user-attachments/assets/e814ed0a-72ce-43ad-80bf-5f03b7f16b90)

[→ XLeRobot で探す](https://github.com/Vector-Wangel/XLeRobot/tree/main/hardware)
</details>

## モーターのデバッグ
デバッグには、Windows PC を USB 接続してサーボのプログラム・試験ができます。[Feetech ソフトウェア](https://www.feetechrc.com/software.html) をダウンロードしてください。Ubuntu では [FT_SCServo_Debug_Qt](https://github.com/Kotakku/FT_SCServo_Debug_Qt) が使えます。LeRobot ライブラリでもモーター設定はできるので必須ではありませんが、不具合調査には便利です。
