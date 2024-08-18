# cs231n - docs

cs231nの日本語訳教材。

## 使用方法

### 依存関係のインストール

```shell
poetry install --only docs
```

`pip`を使用する場合：

```shell
pip install mkdocs mkdocs-material
```

`pip`を使用する場合、最新の依存関係は[`pyproject.toml`](https://github.com/tpu-dsg/cs231n/blob/docs/pyproject.toml)で確認してください。

### プレビューサーバーの起動

```shell
mkdocs serve
```

### ビルド

```shell
mkdocs build
```

## 参考資料

- [MkDocs](https://www.mkdocs.org/)
- [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/)
- [MkDocsによるドキュメント作成 by mebiusbox](https://zenn.dev/mebiusbox/articles/81d977a72cee01)