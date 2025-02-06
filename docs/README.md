# cs231n - docs

cs231nの日本語訳教材。

## 使用方法

### 依存関係のインストール

```shell
uv sync --group docs
# または最小限のパッケージのみをインストールする
uv sync --only-group docs
```

### プレビューサーバーの起動

```shell
uv run mkdocs serve
```

### ビルド

```shell
uv run mkdocs build
```

## 参考資料

- [MkDocs](https://www.mkdocs.org/)
- [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/)
- [MkDocsによるドキュメント作成 by mebiusbox](https://zenn.dev/mebiusbox/articles/81d977a72cee01)