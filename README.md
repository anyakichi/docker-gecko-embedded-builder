# docker-gecko-embedded-builder

## 事前準備

din コマンドを PATH の通った場所に配置してください。

```
$ curl -o ~/.local/bin/din https://raw.githubusercontent.com/anyakichi/docker-buildenv/master/din.sh
```

## RZ/G2E (ek874) 向けの Firefox 60 ESR を含んだビルド

以下のコマンドを実行してください。

```
$ mkdir rzg2e-esr60 && cd rzg2e-esr60
$ din anyakichi/gecko-embedded-builder:rzg2-esr60
builder@rzg2e-esr60:/build$ extract
builder@rzg2e-esr60:/build$ setup
builder@rzg2e-esr60:/build/build$ build
```

実際には extract 後に proprietary なファイルを手動で配置するようメッセー
ジが出るので、それに従って proprietary なファイルの配置を行ってください。

最後の build コマンドは代わりに bitbake コマンドを直接実行しても構いませ
ん。

```
builder@rzg2e-esr60:/build/build$ bitbake core-image-weston
```

## RZ/G2E (ek874) 向けの Firefox 68 ESR を含んだビルド

din に指定するイメージを anyakichi/gecko-embedded-builder:rzg2-esr68 に
変更してビルドしてください。

```
$ mkdir rzg2e-esr68 && cd rzg2e-esr68
$ din anyakichi/gecko-embedded-builder:rzg2-esr68
builder@rzg2e-esr68:/build$ extract
builder@rzg2e-esr68:/build$ setup
builder@rzg2e-esr68:/build/build$ build
```

## RZ/G2E (ek874) 向けの Firefox を含まないビルド

din に指定するイメージを anyakichi/gecko-embedded-builder:rzg2 に変更し
てビルドしてください。

## ビルドの再開

コンテナを終了してもファイル一式は残っているので、いつでも終了して構い
ません。ビルドを再開するには元のディレクトリに戻ってから din コマンドを
実行します。

```
$ cd /path/to/rzg2e-esr60
$ din anyakichi/gecko-embedded-builder:rzg2-esr60
builder@rzg2e-esr60:/build$ setup
builder@rzg2e-esr60:/build/build$ build
```

extract は既に実行済みであれば（ソースコードは既に展開されているので）
再度実行する必要はありません。
