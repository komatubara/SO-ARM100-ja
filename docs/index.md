---
title: 低コストで作れる学習用ロボットアーム
eyebrow: SO-ARM100 日本語ガイド
lead: SO-101 は、自分で印刷・組み立てて、Hugging Face の LeRobot で模倣学習できるオープンハードウェアです。このサイトは原本リポジトリの非公式日本語解説です。
---

<div class="hero">
  <div>
    <p>リーダー（操作側）を手で動かすと、フォロワー（作業側）が同じ動きをします。その動きとカメラ映像をデータとして集め、ニューラルネットワークに「この作業のやり方」を覚えさせる、というのが基本の流れです。</p>
    <p>新品のキットを買うことも、部品を自分で揃えて 3D プリントすることもできます。日本からは秋月電子のリンクが原本に載っています。</p>
  </div>
  <div class="hero-photos">
    <img src="https://raw.githubusercontent.com/TheRobotStudio/SO-ARM100/main/media/SO101_Follower.webp" alt="SO-101 フォロワーアーム">
    <img src="https://raw.githubusercontent.com/TheRobotStudio/SO-ARM100/main/media/SO101_Leader.webp" alt="SO-101 リーダーアーム">
  </div>
</div>

<div class="cards">
  <a class="card" href="{{ '/overview/' | relative_url }}">
    <strong>このロボットとは</strong>
    <span>リーダーとフォロワー、LeRobot、SO-100 と SO-101 の違い。</span>
    <em>まず読む →</em>
  </a>
  <a class="card" href="{{ '/parts/' | relative_url }}">
    <strong>部品を揃える</strong>
    <span>キット販売元と、自分で買う場合の部品表。日本向けリンクあり。</span>
    <em>買う →</em>
  </a>
  <a class="card" href="{{ '/printing/' | relative_url }}">
    <strong>3Dプリント</strong>
    <span>推奨設定、ゲージでの精度確認、印刷サービス。</span>
    <em>印刷する →</em>
  </a>
  <a class="card" href="{{ '/assembly/' | relative_url }}">
    <strong>組み立て（本編）</strong>
    <span>Hugging Face 公式ガイドの日本語訳。動画つきで関節ごとに組む。</span>
    <em>組む →</em>
  </a>
  <a class="card" href="{{ '/software/' | relative_url }}">
    <strong>LeRobot 導入</strong>
    <span>conda / pip、Feetech SDK、ffmpeg。</span>
    <em>入れる →</em>
  </a>
  <a class="card" href="{{ '/train/' | relative_url }}">
    <strong>データ収集と学習</strong>
    <span>テレオペ、記録、ACT 学習、実機推論。</span>
    <em>動かす →</em>
  </a>
</div>

## 最短ルート

<ol class="steps">
  <li>キットを買うか、サーボ・制御ボード・電源・クランプを揃える。</li>
  <li>PLA+ でフレームを印刷する。プリンタが無ければ印刷サービスかプリント済みキット。</li>
  <li>モーターに ID を振り、関節 1 からグリッパーまで組み立てる。</li>
  <li>LeRobot で校正し、テレオペでデータを取る。</li>
  <li>学習して、フォロワー単体で同じ作業を再生する。</li>
</ol>

<div class="callout">
  <strong>原本と一次情報。</strong> ハードウェアファイルは <a href="https://github.com/TheRobotStudio/SO-ARM100">TheRobotStudio/SO-ARM100</a>、組み立てとソフトウェアの詳細は <a href="https://huggingface.co/docs/lerobot/so101">Hugging Face の SO-101 ガイド</a> が公式です。このサイトはそれを日本語で辿りやすくしたものです。英語原文の Markdown はリポジトリ内の <code>*.en.md</code> に残してあります。
</div>

## このサイトで扱うこと

- [部品表と日本からの購入]({{ '/parts/' | relative_url }})
- [印刷設定と外注]({{ '/printing/' | relative_url }})
- [組み立て（Hugging Face チュートリアル日本語訳・動画つき）]({{ '/assembly/' | relative_url }})
- [LeRobot 導入]({{ '/software/' | relative_url }})
- [データ収集と学習]({{ '/train/' | relative_url }})
- [校正（WebUI 3 点法）]({{ '/calibration/' | relative_url }})
- [カメラや柔軟グリッパーなどの拡張]({{ '/optional/' | relative_url }})
- [URDF / MuJoCo]({{ '/simulation/' | relative_url }})
- [よくあるつまずき]({{ '/troubleshooting/' | relative_url }})
