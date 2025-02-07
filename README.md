# cs231n

[![Licence](https://img.shields.io/github/license/tpu-dsg/cs231n)](./LICENSE)
[![CI](https://github.com/tpu-dsg/cs231n/actions/workflows/ci.yaml/badge.svg)](https://github.com/tpu-dsg/cs231n/actions/workflows/ci.yaml)
[![Docs](https://github.com/tpu-dsg/cs231n/actions/workflows/docs.yaml/badge.svg)](https://github.com/tpu-dsg/cs231n/actions/workflows/docs.yaml)

スタンフォード大学の講義 [cs231n: Deep Learning for Computer Vision](https://cs231n.stanford.edu/) の日本語訳

## 実行方法

### Google Colaboratory

1. 「Code」ボタンをクリックしてコードをダウンロードします。
2. ダウンロードしたassignmentのフォルダをGoogleドライブにアップロードします。
3. GoogleドライブからJupyter Notebookファイル(`*.ipynb` )を開きます。
4. 先頭のセル中のパスを適切なものに変更します。

### Dev Container

DockerとVSCodeを用いたモダンな実行環境です。

#### 前提条件

以下が必要です。

- CUDA対応GPU
- Docker
- [NVIDIA Container Toolkit](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/install-guide.html)
- Visual Studio Code

#### 手順

1. VSCodeに[Remote Development拡張機能](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack)をインストールします。
2. リポジトリをローカルにダウンロードしてVSCodeで開きます。
3. トースト通知の「コンテナーで再度開く」をクリックします。

### Jupyter Lab

Anacondaのインストール不要で[Jupyter Lab](https://jupyter.org/)の実行環境が起動できます。

#### 前提条件

以下が必要です。

- CUDA対応GPU
- [uv](https://docs.astral.sh/uv/)

#### 手順

1. 「Code」ボタンをクリックしてコードをダウンロードします。
2. ターミナルでリポジトリまで移動します。
3. 以下のコマンドを**順番に**実行し、Jupyter Labを起動します。表示されたURLにアクセスしてください。

   ```bash
    uv sync
    uv run ipython kernel install --user --env VIRTUAL_ENV $(pwd)/.venv --name=project
    uv run --with jupyter jupyter lab
   ```

### その他の方法

「Dockerを用いないVSCode環境」など、お好きな実行環境が使用できます。

#### 前提条件

以下が必要です。

- CUDA対応GPU
- [uv](https://docs.astral.sh/uv/)

#### 手順

1. 「Code」ボタンをクリックしてコードをダウンロードします。
2. ターミナルでリポジトリまで移動します。
3. 以下のコマンドを実行し、依存するパッケージをインストールします。

   ```bash
    uv sync
   ```

## 教材

- [講義資料（英語）](https://cs231n.stanford.edu/schedule.html)
- [講義資料（日本語）](https://tpu-dsg.github.io/cs231n)
- [2017年講義動画（英語）](https://youtube.com/playlist?list=PLC1qU-LWwrF64f4QKQT-Vg5Wr4qEE1Zxk&si=A-w05a3qxL9TKhBu)

日本語の講義資料はこのリポジトリで管理されています。詳しくは[こちら](./docs/README.md)をご覧ください。

## 貢献方法

[リポジトリへの貢献ガイド](https://github.com/tpu-dsg/.github/blob/main/CONTRIBUTING.md)を参照してください。

コミット前には、以下のコマンドでNotebookの不要なメタデータの削除とコードスタイルのフォーマットを行ってください。

```bash
nbdev_clean
ruff format .
```
