---
title: 部品を揃える
eyebrow: 調達
lead: 完成キット、プリント済みフレーム、電子部品だけ、の 3 段階があります。日本からは秋月電子が原本の JP 列に入っています。
---

## 買うか、自分で揃えるか

- **完成アーム** — 組み立て済み。WowRobo、PartaBot など。
- **3D プリント済みフレーム + 電子部品** — Seeed Studio / 秋月電子のキットがこの系統です。
- **完全自作** — サーボとボードを通販し、STL を自分で印刷する。

テレオペで学習する定番構成は **フォロワー 1 本 + リーダー 1 本** です。VR で操作するならフォロワーだけでも使えます（Phospho のフォロワー単体キットなど）。

## 日本から買いやすい入口

原本の部品表にある JP リンクの例です。在庫と価格は変動します。

- [Seeed の SO-ARM100 キット（秋月電子）](https://akizukidenshi.com/catalog/g/g131169/)
- [STS3215 7.4V 1/345（C001）](https://akizukidenshi.com/catalog/g/g116312/)
- [STS3215 7.4V 1/191（C044）](https://akizukidenshi.com/catalog/g/g131131/)
- [STS3215 7.4V 1/147（C046）](https://akizukidenshi.com/catalog/g/g131132/)
- [モーター制御ボード](https://akizukidenshi.com/catalog/g/g131227/)
- [電源](https://akizukidenshi.com/catalog/g/g106238/)

Seeed キットは 3D プリント部品中心です。サーボ本数やリーダー用のギア比違いをキット内容と照合してください。

## キット販売元（原本掲載）

- [RobotEd（スイス）](https://roboted.ch/en/shop/so-101-robot-arm-kit) — フレーム / 電子部品 / 完成アーム
- [Robonine](https://robonine.com/) — 部品キット
- [PartaBot（米国）](https://partabot.com) — 組み立て済み。LeKiwi や Koch も
- [ForgeMotion Labs](https://forgemotionlabs.com/products) — フレーム / 電子部品 / 完成アーム
- [Seeed Studio](https://www.seeedstudio.com/SO-ARM100-Low-Cost-AI-Arm-Kit.html) / [秋月](https://akizukidenshi.com/catalog/g/g131169/)
- [WowRobo](https://shop.wowrobo.com/products/so-arm101-diy-kit-assembled-version-1) — 組み立て済み
- [RoboSEasy（韓国）](https://smartstore.naver.com/roboseasy)
- [NeoBot（中国）](https://item.taobao.com/item.htm?ft=t&id=957685951340)
- [Autodiscovery（EU）](https://autodiscovery.eu/en/products/so-101-kit??utm_source=hf&utm_medium=shop&utm_content=web)
- フォロワーのみ: [Phospho](https://robots.phospho.ai)

## 2 本アームを自分で揃える場合

概算（原本掲載、地域で変動）:

- 米国: 約 $230
- EU: 約 €226
- 日本: 約 ￥44,530

内訳の要点:

| 部品 | 数量 | 役割 |
| --- | ---: | --- |
| STS3215 7.4V 1/345 (C001) | 7 | フォロワー 6 + リーダーの肩上げ 1 |
| STS3215 7.4V 1/191 (C044) | 2 | リーダーの土台旋回と肘 |
| STS3215 7.4V 1/147 (C046) | 3 | リーダーの手首 2 + グリッパー 1 |
| モーター制御ボード | 2 | アームごとに 1 枚。Waveshare 系 |
| USB-C ケーブル | 2 本セット ×1 | PC 接続 |
| 電源 | 2 | アームごとに 1 |
| テーブルクランプ | 4 | ベース固定 |
| プラスドライバー #0 / #1 | 1 セット | 必須に近い |

リーダー用サーボ 6 個は [Alibaba のセット](https://www.alibaba.com/product-detail/6PCS-7-4V-STS3215-Servos-for_1601428584027.html) でもまとめて買えます。

<div class="callout">
  <strong>電圧に注意。</strong> フォロワーは 7.4V 版（ストール約 16.5kg·cm @ 6V）が標準です。より力が欲しければ 12V 版（約 30kg·cm）もありますが、電源も 12V 5A 以上に替える必要があります。リーダーは SO-101 では常に 7.4V です。混ぜないでください。
</div>

フォロワー 1 本だけの部品表は、サーボ 6（すべて 1/345）、ボード 1、電源 1、クランプ 2 です。原本 README の表に US / EU / CN / JP の購入リンクがあります。

## ドライバー

指定セットそのものは不要ですが、**プラス #0 と #1** がないと Feetech 付属ネジが扱いづらいです。
