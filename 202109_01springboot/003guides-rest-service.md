# Spring 公式ガイドを観る No.1: Building a RESTful Web Service

- YouTube リンク
  - https://www.youtube.com/watch?v=E-ICm9lBgFg
- 資料
  - [Getting Started | Building a RESTful Web Service](https://spring.io/guides/gs/rest-service/) ([日本語バージョン](https://spring.pleiades.io/guides/gs/rest-service/))
  - [Java SE 日本語ドキュメント](https://www.oracle.com/jp/java/technologies/documentation.html) > [Java11 API 仕様](https://docs.oracle.com/javase/jp/11/docs/api/index.html)

## 前回の補遺: Windows Terminal インストールとセットアップ (00:00)

### プログラミング用フォントインストール

動画の説明とは順序が変わりますが、先にフォントをインストールしておきます。

プログラミング用フォントであれば何でも良いですが、今回は Cica をインストールし使用することにします。

(なお、 Cica 以外にどんなフォントがあるか知りたい場合は "プログラミング用フォント" といったキーワードで検索してみてください。無料で利用できるものも多数あります。)

- https://github.com/miiton/Cica/releases

上のページから最新版の zip ファイルをダウンロードします。
本ドキュメント記載時点では [`Cica_v5.0.2_with_emoji.zip`](https://github.com/miiton/Cica/releases/download/v5.0.2/Cica_v5.0.2_with_emoji.zip) です。

ダウンロードした `.zip` ファイルを展開し、 `Cica-Regular.ttf` をダブルクリックするとウィンドウが開きますので、 "インストール" ボタンを押してインストールします。

### Windows Terminal インストール

PowerShell Core を起動し、以下のコマンドでインストールします:

```
scoop install windows-terminal
```

### Windows Terminal セットアップ

- 参考: [Adding Git-Bash to the new Windows Terminal](https://stackoverflow.com/a/57369284/4506703) - Stack Overflow

1. Windows Terminal を起動し、 `Ctrl` + `,` キーを押して設定画面を開きます。
1. "新しいプロファイルを追加します" を押し、既存のプロファイルを "複製" し、そのまま "保存" します。
1. "JSON ファイルを開く" を押し、 VSCode で開きます。

`name` が "`PowerShell (\u30b3\u30d4\u30fc)`"(上で複製したものです)となっているものを探し、`commandline`, `icon`, `name` の値をそれぞれ次の通りに設定します。
(これら以外の項目は変更せずに残しておいてください。)

```
"commandline": "%USERPROFILE%/scoop/apps/git/current/usr/bin/bash.exe -l -i",
"icon": "%USERPROFILE%/scoop/apps/git/current/usr/share/git/git-for-windows.ico",
"name": "Git Bash",
```

続いて、同じプロファイル設定に `fontFace` 項目を追加します。ここでは先にインストールしておいた Cica フォントを指定します。

```
fontFace: "Cica"
```

最後に、デフォルトで起動するプロファイルをこの "Git Bash" に指定しておきます。Windows Terminal の設定画面で "スタートアップ" を選択し、 "既定のプロファイル" で "Git Bash" を選択します。

## 本題に入る前に: 公式ガイドの読み進め方

各ガイドには Git リポジトリが付属していて、少なくとも初期状態のコード(initial)と、最終的な状態のコード(complete)が格納されています。

初期状態のコードは、写経する上で本質的でない部分をスキップするのに役立ちます。

最終状態のコードは実行可能で、このガイドが何を説明したいかを実際に動かしてみながら確認するのに役立ちます。

complete ディレクトリのコードを動かしてみて全体像を掴んでから本文を読み進めていくのがお勧めです(ガイド文章の構成もそのようになっているはずです)。

## Building a RESTful Web Service

- [Spring Initializr](https://start.spring.io/) の使い方
-
