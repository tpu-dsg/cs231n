# cs231n - docs

cs231nの日本語訳教材。

## 必要要件

日本語訳教材をローカルでプレビューするには以下が必要です。

- [mdBook](https://github.com/rust-lang/mdBook)
  - [mdbook-mermaid](https://github.com/badboy/mdbook-mermaid)
  - [mdbook-admonish](https://github.com/tommilligan/mdbook-admonish)
  - [mdbook-toc](https://github.com/badboy/mdbook-toc)

Dockerユーザであれば[`compose.yaml`](./compose.yaml)を利用できるので環境構築の必要はありません。

## 使用方法

以下のコマンドを実行後[http://localhost:3000/](http://localhost:3000/)にアクセスすることでプレビューできます。

```shell
cd docs
# Docker
docker compose up
# Docker以外
mdbook serve --hostname '0.0.0.0'
```

ビルドのみの場合は以下を実行してください。

```shell
# Docker
docker compose run --rm mdbook build
# Docker以外
mdbook build
```

Dockerは以下の例のような`docker.env`ファイルを`docs/`直下に作成することで、一般ユーザで実行できます。`USERID`、`GROUPID`の値はぞれぞれ`id -u`、`id -g`コマンドで取得したものを使用してください。

```shell
USERID=1000
GROUPID=1000
```

## 参考資料

この日本語訳教材は以下の記法をサポートしています。

- [Markdown - mdBook Documentation](https://rust-lang.github.io/mdBook/format/markdown.html)
- [MathJax - mdBook Documentation](https://rust-lang.github.io/mdBook/format/mathjax.html)
- [Mermaid](https://mermaid.js.org/intro/)
  - ([mdbook-mermaid](https://github.com/badboy/mdbook-mermaid)によってサポート)
- [mdbook-admonish](https://tommilligan.github.io/mdbook-admonish/)
- [mdbook-toc](https://github.com/badboy/mdbook-toc)

`compose.yaml`では以下のイメージを使用しています。

- [peaceiris/mdbook - Docker Hub](https://hub.docker.com/r/peaceiris/mdbook) ([リポジトリ](https://github.com/peaceiris/docker-mdbook))
