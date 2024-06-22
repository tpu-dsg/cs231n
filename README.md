# cs231n

[![Licence](https://img.shields.io/github/license/tpu-dsg/cs231n)](./LICENSE)

スタンフォード大学の講義 [cs231n: Deep Learning for Computer Vision](https://cs231n.stanford.edu/) の日本語訳

## 実行方法

### Google Colaboratory

1. 「Code」ボタンをクリックしてコードをダウンロードします。
2. ダウンロードしたassignmentのフォルダをGoogleドライブにアップロードします。
3. GoogleドライブからJupyter Notebookファイル(`*.ipynb` )を開きます。
4. 先頭のセル中のパスを適切なものに変更します。

### Docker（ローカル）

Docker・[NVIDIA Container Toolkit](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/install-guide.html)(GPUマシンのみ)・VSCodeをインストール済みの場合は、Devcontainerを使用して動かすことができます。

1. VSCodeに[Remote Development拡張機能](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack)をインストールします。
2. リポジトリをローカルにダウンロードしてVSCodeで開きます。
3. トースト通知の「コンテナーで再度開く」をクリックします。

## 教材

- [講義資料(英語)](https://cs231n.stanford.edu/schedule.html)
- [2017年講義動画(英語)](https://youtube.com/playlist?list=PLC1qU-LWwrF64f4QKQT-Vg5Wr4qEE1Zxk&si=A-w05a3qxL9TKhBu)

## 貢献方法

[リポジトリへの貢献ガイド](https://github.com/tpu-dsg/.github/blob/main/CONTRIBUTING.md)を参照してください。

コードの品質を保つために`pre-commit`を使用しています。`*ipynb`,`*.py`ファイルをコミットする前に以下の手順で`pre-commit`をセットアップしてください。（Dockerでは自動でセットアップされるので`poetry shell`を実行するだけです！）

1. 依存関係のインストール

    リポジトリの`pyproject.toml`を使用している場合はインストール済みなので不要です。
    ```bash
    pip install pre-commit nbdev ruff
    ```

2. Git フックのインストール

    Poetry環境は事前に`poetry shell`を実行してください。
    ```bash
    pre-commit install
    ```

これでコミット時にJupyter Notebookの不要なメタデータの削除とコードフォーマットが行われるようになりました。コミット時に`pre-commit`が**Failed**となった場合は新たな差分ができているので、ステージして再コミットしてください。