# docker-gecko-embedded-builder

## 事前準備

din コマンドを PATH の通った場所に配置してください。

```
$ curl -o ~/.local/bin/din https://raw.githubusercontent.com/anyakichi/docker-buildenv/master/din.sh
```

## ek874 向けの BSP-1.0.1 に Firefox 60 ESR を含めたビルド

以下のコマンドを実行してください。

```
$ mkdir ek874-esr60 && cd ek874-esr60
$ din anyakichi/gecko-embedded-builder:ek874-101-esr60
builder@ek874-esr60:/build$ extract
builder@ek874-esr60:/build$ setup
builder@ek874-esr60:/build/build$ build
```

実際には extract 後に proprietary なファイルを手動で配置するようメッセー
ジが出るので、それに従って proprietary なファイルの配置を行ってください。

最後の build コマンドは代わりに bitbake コマンドを直接実行しても構いませ
ん。

```
builder@ek874-esr60:/build/build$ bitbake core-image-weston
```

## hihope-rzg2m 向けの BSP-1.0.1-update1 に Firefox 68 ESR を含めたビルド

din に指定するイメージを
anyakichi/gecko-embedded-builder:hihope-rzg2m-101u1-esr68 に変更してビルドして
ください。

```
$ mkdir hihope-rzg2m-101u1-esr68 && cd hihope-rzg2m-101u1-esr68
$ din anyakichi/gecko-embedded-builder:hihope-rzg2m-101u1-esr68
builder@hihope-rzg2m-101u1-esr68:/build$ extract
builder@hihope-rzg2m-101u1-esr68:/build$ setup
builder@hihope-rzg2m-101u1-esr68:/build/build$ build
```


## その他のビルド

使用するイメージを変更することで、ターゲットボード・BSP バージョン・
Firefox バージョンのそれぞれ異なる FW の作成が行なえます。指定可能な組は
Dockerhub のタグから確認してください。

https://hub.docker.com/r/anyakichi/gecko-embedded-builder/tags


## ビルドの再開

コンテナを終了してもファイル一式は残っているので、いつでも終了して構い
ません。ビルドを再開するには元のディレクトリに戻ってから din コマンドを
実行します。

```
$ cd /path/to/ek874-esr60
$ din anyakichi/gecko-embedded-builder:ek874-101-esr60
builder@ek874-esr60:/build$ setup
builder@ek874-esr60:/build/build$ build
```

extract は既に実行済みであれば（ソースコードは既に展開されているので）
再度実行する必要はありません。


## パフォーマンスについて

一部のディストリビューションにおいて Docker で overlayfs を使用している
場合、コンテナが起動してプロンプトが出るまでに非常に時間がかかる場合があ
ります。

パフォーマンスが出ない場合には、overlayfs のモジュールパラメーターを調整
すると改善する可能性があります。

```
$ sudo vi /etc/modprobe.d/overlay.conf
options overlay redirect_dir=Y metacopy=Y
```
