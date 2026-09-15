---
title: LeRobot の導入
eyebrow: Hugging Face チュートリアル
lead: Hugging Face のインストールガイドを、SO-101 で使う範囲に絞って日本語にしたものです。Python 3.12 以上、PyTorch 2.10 以上が前提です。
---

<p class="source-note">非公式訳です。原本は <a href="https://huggingface.co/docs/lerobot/installation">huggingface.co/docs/lerobot/installation</a>。環境構築の細部は原本の方が新しいことがあります。</p>

公式は `conda`（miniforge）を推奨しています。`uv` や `venv` でも構いません。Python >= 3.12 と PyTorch >= 2.10 を満たしたら、手順 2 の環境作成へ進んでください。

## 手順 1（conda のとき）: miniforge を入れる

```bash
wget "https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-$(uname)-$(uname -m).sh"
bash Miniforge3-$(uname)-$(uname -m).sh
```

## 手順 2: 仮想環境

Python 3.12 の環境を作ります。

```bash
conda create -y -n lerobot python=3.12
conda activate lerobot
```

`uv` の場合:

```bash
uv python install 3.12
uv venv --python 3.12
# Linux / macOS
source .venv/bin/activate
# Windows PowerShell
# .venv\Scripts\activate
```

シェルを開くたびに activate が必要です。

WSL では `evdev` も入れてください。

```bash
# conda
conda install evdev -c conda-forge
# uv
sudo apt install libevdev-dev
uv pip install evdev
```

### ffmpeg（動画デコード）

LeRobot は既定で [TorchCodec](https://github.com/meta-pytorch/torchcodec) を使い、`ffmpeg` が必要です。

TorchCodec が使えない環境（macOS Intel、Linux ARM、PyTorch < 2.8 の Windows）では自動で `pyav` に落ちるので、ffmpeg は飛ばして手順 3 へ進んで構いません。

使える環境では、conda に入れる方法がどの PyTorch でも動きます。**PyTorch < 2.10 では必須**です。

```bash
conda install ffmpeg -c conda-forge
```

`libsvtav1` が無い、`torchcodec` とバージョンが合わない、といったときは:

```bash
conda install ffmpeg=7.1.1 -c conda-forge
```

PyTorch >= 2.10（TorchCodec ≥ 0.10）なら、システムの ffmpeg を動的リンクできます。

```bash
# Ubuntu / Debian
sudo apt install ffmpeg
# macOS Apple Silicon
brew install ffmpeg
```

システムの ffmpeg は **PyTorch >= 2.10 だけ** です。古い PyTorch は conda の ffmpeg を使います。

## 手順 3: LeRobot を入れる

本体は軽量で、重い依存は extras に分かれています。

### ソースから（推奨）

```bash
git clone https://github.com/huggingface/lerobot.git
cd lerobot
pip install -e ".[core_scripts]"  # 記録・再生・校正
pip install -e ".[training]"      # 学習
pip install -e ".[feetech]"       # SO-101 のモーター
```

全部入れるなら `pip install -e ".[all]"`。`uv` なら `uv pip install -e ".[core_scripts]"` のように置き換えます。

### PyPI から

```bash
pip install 'lerobot[core_scripts,feetech]'
pip install 'lerobot[training]'
```

| extra | 入るもの | 用途 |
| --- | --- | --- |
| `dataset` | datasets, av, torchcodec, jsonlines | データセット |
| `training` | dataset + accelerate, wandb | 学習 |
| `hardware` | pynput, pyserial, deepdiff | 実機接続 |
| `viz` | rerun-sdk | 記録・評価の可視化 |
| `core_scripts` | dataset + hardware + viz | record / replay / calibrate |
| `feetech` | Feetech SDK | SO-100 / SO-101 / Moss |

### CUDA（Linux）

ソースを `uv` で入れると、プロジェクトは CUDA 12.8 の PyTorch（ドライバ下限 570.86）にピン止めされます。PyPI の既定 Linux ホイールは cu130 系（ドライバ下限 580.65）です。ドライバに合わせて変える例:

```bash
pip install --index-url https://download.pytorch.org/whl/cu128 torch torchvision
pip install -e ".[all]"
```

### ビルドで落ちるとき

Linux では次が必要になることがあります。

```bash
sudo apt-get install cmake build-essential python3-dev pkg-config \
  libavformat-dev libavcodec-dev libavdevice-dev libavutil-dev \
  libswscale-dev libswresample-dev libavfilter-dev
```

学習のログに Weights & Biases を使うなら `wandb login` します。`training` extra に含まれます。

次は [組み立て]({{ '/assembly/' | relative_url }}) でモーター ID を振り、関節を組みます。
