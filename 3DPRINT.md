# 3D プリントサービス

部品を 3D プリントしてもらう方法はいくつかあります。検証できたものから順に載せています。別のサービスを試した方は、追加できるよう教えてください。SeeedStudio はプリント済み部品単体も販売しています: [SO-ARM100 3D-Printed Enclosure](https://www.seeedstudio.com/SO-ARM100-3D-printed-Enclosure-p-6409.html)。

- [ヨーロッパ](#craftcloud3d)（Craftcloud3d） :fr: :de: :uk: :it: :es:
- [米国](#craftcloud3d)（Craftcloud3d） :us:
- [中国](#pcbway)（PCBWay） :cn:

### [Craftcloud3d](https://craftcloud3d.com)
**Craftcloud** は、注文を各国の製造パートナーへ振り分けるマーケットプレイスです。柔軟に使えますが、価格は変動します。

部品を作るには [craftcloud3d.com](https://craftcloud3d.com/upload) に行き、`STL/SO101/Individual/` の個別部品ファイルをアップロードします。部品は 14 種類（共通 9 点 + リーダー専用 + フォロワー専用）です。内訳は README の [個別部品ファイル](README.md#手順-4-部品を印刷する) を見てください。注意点:

- `SO101 Assembly.stl` は **アップロードしない** でください。アーム全体の参考モデルで、印刷対象ではありません。
- マウントプレートは **どちらか一方だけ** です。サーボドライバ基板に合わせて `WaveShare_Mounting_Plate_SO101.stl` **または** `Seeedstudio_Mounting_Plate_SO101.stl` を選んでください。
- 共通 9 点は **両アームで使う** ので、リーダー + フォロワーを作る場合は数量を **2** にしてください。

アップロード画面:

![Craftcloud3d](./media/3dprinting/craftcloud1.png)

`See Materials & Pricing` を押し、次のページで材料を選びます。今回は `PLA+` です。

![Craftcloud3d](./media/3dprinting/craftcloud2.png)

`Select Material` を押し、仕上げを選びます。
- `Finish` = Standard
- `Infill` = 20%（インフィル選択肢が見えない場合は、価格計算が終わるまで待つ）

`Select Finish` で次へ進みます。

![Craftcloud3d](./media/3dprinting/craftcloud3.png)

色を選び、`See offers` をクリックします。

![Craftcloud3d](./media/3dprinting/craftcloud4.png)

最後に製造元を選びます。価格・納期・生産地で比較できます。

![Craftcloud3d](./media/3dprinting/craftcloud5.png)

これで完了です。部品が届いたら SO-101 の組み立てに進めます。

### [PCBWay](https://www.pcbway.com)
**PCBWay** は世界発送できますが、中国以外では輸入税がかかるため、結果的に高くなりがちです。

部品を作るには [pcbway.com](https://www.pcbway.com/rapid-prototyping/manufacture/?type=2) に行き、一体型プレートファイル `STL/SO101/Leader/Ender_Leader_SO101.stl` と `STL/SO101/Follower/Ender_Follower_SO101.stl` の 2 つをアップロードします。

![PCBWay](./media/3dprinting/pcb_way.png)

次の設定にします。
- `Quantity` = 両方とも 1（必要なら増やす）
- `Design Units` = mm
- `Material` → Custom material → `PLA+` と入力
- `Product Desc` → DIY Entertainment → Robot components
- `Other special requests` = `FDM, 20% infill`（希望色もここに書けます）

これで [FDM](https://www.hubs.com/knowledge-base/what-is-fdm-3d-printing/) の 3D プリント、インフィル 20% を指定したことになります。他の項目はそのままで構いません。確認したら `Submit` をクリックします。

![PCBWay](./media/3dprinting/pcb_way2.png)

検証後、送料込みの最終見積が出ます。価格は変動しますが、リーダー + フォロワーでおよそ 95 ドル前後だった、というのが原文の経験です。連絡は PCBWay のオンラインポータルからできます。

![PCBWay](./media/3dprinting/pcb_way3.png)
