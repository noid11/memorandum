何度も調べたくない事の備忘録。

# TOC

<!-- TOC -->

- [TOC](#toc)
- [`javascript`](#javascript)
    - [JSON を pretty print したい](#json-を-pretty-print-したい)
- [`python`](#python)
    - [`python -m json.tool`: jq が無い環境で json を見やすく表示する](#python--m-jsontool-jq-が無い環境で-json-を見やすく表示する)
    - [`python -m http.server 8000`: http server をサクッと動かす](#python--m-httpserver-8000-http-server-をサクッと動かす)
- [`npm`: Node Package Manager](#npm-node-package-manager)
    - [`npm` cli](#npm-cli)
        - [`npm init`, `npm install package-name`: 初期セットアップ](#npm-init-npm-install-package-name-初期セットアップ)
        - [`npm install package-name@xxx`: バージョンを指定してパッケージをインストールする](#npm-install-package-namexxx-バージョンを指定してパッケージをインストールする)
    - [`npx`: execute npm package binaries](#npx-execute-npm-package-binaries)
- [Visual Studio Code](#visual-studio-code)
    - [Extensions](#extensions)
        - [Whitespace+: スペースやタブに色付けしてくれる](#whitespace-スペースやタブに色付けしてくれる)
        - [zenkaku: 全角スペースをハイライトしてくれる](#zenkaku-全角スペースをハイライトしてくれる)
        - [Markdown TOC: 日本語使っててもいい感じに TOC を作ってくれる](#markdown-toc-日本語使っててもいい感じに-toc-を作ってくれる)
    - [ショートカット](#ショートカット)
        - [一覧](#一覧)
        - [`Command + Shift + P`: コマンドパレット](#command--shift--p-コマンドパレット)
        - [`Command + P`: 名前を入力して任意のファイルかシンボルに移動](#command--p-名前を入力して任意のファイルかシンボルに移動)
        - [`control + Tab`: タブ切り替え](#control--tab-タブ切り替え)
        - [`Command + Shift + O`: Markdown の見出しをベースに移動できる。正確にはファイル内のシンボル移動](#command--shift--o-markdown-の見出しをベースに移動できる正確にはファイル内のシンボル移動)
        - [`control + G`: 特定行に移動](#control--g-特定行に移動)
        - [`Command + K -> Z`: Zen Mode](#command--k---z-zen-mode)
        - [`Command + Shift + [`, `Command + option + right` タブの左右移動](#command--shift---command--option--right-タブの左右移動)
- [`docker`](#docker)
    - [`jshell` をサクッと使いたい](#jshell-をサクッと使いたい)
    - [docker official images](#docker-official-images)
    - [Apache(httpd) をサクッと動かす](#apachehttpd-をサクッと動かす)
    - [nginx をサクッと動かす](#nginx-をサクッと動かす)
    - [MySQL をサクッと動かす](#mysql-をサクッと動かす)
    - [PostgreSQL をサクッと動かす](#postgresql-をサクッと動かす)
- [`echo`](#echo)
    - [`echo -n 'hoge'`: 改行を出力しない](#echo--n-hoge-改行を出力しない)
    - [`echo -e 'hoge\nfuga'`: 改行を出力する](#echo--e-hoge\nfuga-改行を出力する)
- [`say`: テキスト読み上げ](#say-テキスト読み上げ)
- [`grep`: ファイルのパターンサーチ](#grep-ファイルのパターンサーチ)
    - [`grep -c hoge`: マッチした行カウント](#grep--c-hoge-マッチした行カウント)
    - [`grep -c -v hoge`: マッチしなかった行カウント](#grep--c--v-hoge-マッチしなかった行カウント)
- [`wc`](#wc)
    - [`echo -e '1\n2\n3' | wc -l`: 行数をカウントしたい](#echo--e-1\n2\n3--wc--l-行数をカウントしたい)
    - [`pbpaste | wc -w`: クリップボードにコピーした文字列の長さを知りたい](#pbpaste--wc--w-クリップボードにコピーした文字列の長さを知りたい)
- [`cut`: 受け取った文字列を分割して扱いたい](#cut-受け取った文字列を分割して扱いたい)
- [圧縮, 展開](#圧縮-展開)
    - [zip](#zip)
        - [`zip archived.zip hoge.txt`: ファイル圧縮](#zip-archivedzip-hogetxt-ファイル圧縮)
        - [`zip -r archived.zip ./hogedir`: ディレクトリ圧縮](#zip--r-archivedzip-hogedir-ディレクトリ圧縮)
        - [`zipinfo archived.zip`: 圧縮ファイルの情報を見る](#zipinfo-archivedzip-圧縮ファイルの情報を見る)
    - [`unzip archived.zip`: 圧縮ファイルの展開](#unzip-archivedzip-圧縮ファイルの展開)
- [パフォーマンス系](#パフォーマンス系)
    - [CPU 使用率を上げたい](#cpu-使用率を上げたい)
- [Git](#git)
    - [`.gitignore` あれこれ](#gitignore-あれこれ)
    - [`git rm filename`: Git で管理しているファイルを削除したい](#git-rm-filename-git-で管理しているファイルを削除したい)
    - [`git rm --cached filename`: 特定ファイルを削除せずに Git 管理から外したい](#git-rm---cached-filename-特定ファイルを削除せずに-git-管理から外したい)
    - [`git log -1`, `git log -n 1`: 直前の commit log を見たい](#git-log--1-git-log--n-1-直前の-commit-log-を見たい)
    - [`git diff --cached filename`: add したファイルの diff が見たい](#git-diff---cached-filename-add-したファイルの-diff-が見たい)
    - [ローカルでトピックブランチ作ってマージして消す](#ローカルでトピックブランチ作ってマージして消す)
    - [`git commit --amend -m 'fix message'`: 直前の commit メッセージ変更](#git-commit---amend--m-fix-message-直前の-commit-メッセージ変更)
    - [直前の commit 取り消し](#直前の-commit-取り消し)
    - [ファイルやディレクトリのリネーム](#ファイルやディレクトリのリネーム)
    - [プライベートな GitHub アカウントで使ってる Git ユーザーを設定する](#プライベートな-github-アカウントで使ってる-git-ユーザーを設定する)
- [AWS CLI](#aws-cli)
    - [`aws configure --profile hoge`: profile 追加](#aws-configure---profile-hoge-profile-追加)
    - [AWS CLI で IAM Role のクレデンシャルを使う](#aws-cli-で-iam-role-のクレデンシャルを使う)
    - [Pinpoint](#pinpoint)
        - [`update-endpoint`: エンドポイントの登録、更新](#update-endpoint-エンドポイントの登録更新)
        - [`get-entpoid`: エンドポイント取得](#get-entpoid-エンドポイント取得)
    - [ECS/Fargate](#ecsfargate)
        - [`run-task`: タスク実行](#run-task-タスク実行)
            - [Fargage](#fargage)
            - [EC2](#ec2)
    - [Systems Manager](#systems-manager)
        - [`put-parameter`: パラメーターストアに値を登録、更新](#put-parameter-パラメーターストアに値を登録更新)
        - [`get-parameter`: パラメーターストアの値を取得](#get-parameter-パラメーターストアの値を取得)
    - [Step Functions](#step-functions)
        - [`create-state-machine`: ステートマシーン作成](#create-state-machine-ステートマシーン作成)
        - [`start-execution`: ステートマシーン実行](#start-execution-ステートマシーン実行)
    - [CloudFormation](#cloudformation)
        - [`validate-template`: template 検証](#validate-template-template-検証)
        - [`deploy`: template を使ってデプロイ](#deploy-template-を使ってデプロイ)
        - [`describe-stack-events`: スタックのイベント取得](#describe-stack-events-スタックのイベント取得)
        - [`describe-stack-resources`: スタックのリソース取得](#describe-stack-resources-スタックのリソース取得)
        - [`describe-stacks`: スタック情報取得](#describe-stacks-スタック情報取得)
        - [`delete-stack`: スタック削除。](#delete-stack-スタック削除)
- [AWS Chalice](#aws-chalice)
- [ランダム文字列生成](#ランダム文字列生成)
- [pandoc を使って markdown を XWiki 記法に変換](#pandoc-を使って-markdown-を-xwiki-記法に変換)
    - [参考](#参考)
- [`curl`](#curl)
    - [通信の詳細を見たい](#通信の詳細を見たい)
    - [レスポンスされるステータスコードを見たい](#レスポンスされるステータスコードを見たい)
    - [POST したい](#post-したい)
    - [リクエストをしばらく連続して行いたい](#リクエストをしばらく連続して行いたい)
    - [参考](#参考)
- [`nc`](#nc)
    - [HTTP リクエスト](#http-リクエスト)
    - [サーバーとして待ち受ける、HTTP リクエストをタイムアウトさせたい](#サーバーとして待ち受けるhttp-リクエストをタイムアウトさせたい)
    - [ポート状況の確認](#ポート状況の確認)
    - [参考](#参考)
- [`openssl`](#openssl)
    - [サーバーに設定されている証明書の確認](#サーバーに設定されている証明書の確認)
        - [SNI](#sni)
    - [HTTP リクエスト](#http-リクエスト)
    - [参考](#参考)
- [`date`](#date)
    - [unixtime を JST に変換](#unixtime-を-jst-に変換)
    - [unixtime を UTC に変換](#unixtime-を-utc-に変換)
    - [現在時刻を unixtime で出力](#現在時刻を-unixtime-で出力)
    - [現在時刻を ISO 8601 で出力](#現在時刻を-iso-8601-で出力)
        - [JST](#jst)
        - [UTC](#utc)
    - [参考](#参考)
- [XML を jq 的に整形したい](#xml-を-jq-的に整形したい)
    - [参考](#参考)
- [環境変数一覧を表示したい](#環境変数一覧を表示したい)
- [bash](#bash)
    - [`while`](#while)
    - [`for`](#for)
    - [交互にコマンドを実行するスクリプト](#交互にコマンドを実行するスクリプト)
- [英語](#英語)
    - [苦情とかのクレーム: complaint](#苦情とかのクレーム-complaint)
    - [appearance: 外観](#appearance-外観)
    - [分かりにくくてスマヌ: `Sorry it's hard to understand.`, `Please excuse my lack of explanation.`](#分かりにくくてスマヌ-sorry-its-hard-to-understand-please-excuse-my-lack-of-explanation)
    - [なんか追加で情報必要なら声かけて: If you need additional information, please let me know.](#なんか追加で情報必要なら声かけて-if-you-need-additional-information-please-let-me-know)
    - [再発、再現: recurrent](#再発再現-recurrent)
- [気になったブログ記事など](#気になったブログ記事など)
    - [Ｃプログラミング診断室](#ｃプログラミング診断室)
    - [AWS X-Ray SDK for the Python のローカルサンプリングルール読み込んでいる箇所の実装](#aws-x-ray-sdk-for-the-python-のローカルサンプリングルール読み込んでいる箇所の実装)
    - [MDN まとめ](#mdn-まとめ)
    - [OAuth の Implicit grant と Authorization code grant について](#oauth-の-implicit-grant-と-authorization-code-grant-について)
    - [`0.0.0.0` と `127.0.0.1` と `localhot`](#0000-と-127001-と-localhot)
- [便利な Web サイト](#便利な-web-サイト)
    - [プログラミング言語やフレームワークやツールのリファレンスまとめサイト](#プログラミング言語やフレームワークやツールのリファレンスまとめサイト)
    - [OAuth 2.0, OpenID Connect の技術情報](#oauth-20-openid-connect-の技術情報)
    - [ランダムな JWK (JSON Web Key) を生成できるサイト](#ランダムな-jwk-json-web-key-を生成できるサイト)
    - [AI 生成の顔写真](#ai-生成の顔写真)
    - [AWS のセキュリティを学べるサイト](#aws-のセキュリティを学べるサイト)
    - [JavaScript チートシート](#javascript-チートシート)
    - [迷路生成アルゴリズムのサンプル](#迷路生成アルゴリズムのサンプル)
    - [AWS, GCP, Azure 等のアイコンを使って構成図を作成できるサイト](#aws-gcp-azure-等のアイコンを使って構成図を作成できるサイト)
    - [AWS の構成図を作成できるサイト](#aws-の構成図を作成できるサイト)
    - [AWS を図でまとめているサイト](#aws-を図でまとめているサイト)
    - [AWS のサービスリリース履歴を管理しているサイト](#aws-のサービスリリース履歴を管理しているサイト)
    - [EC2, RDS の Instance 早見表](#ec2-rds-の-instance-早見表)
    - [AWS CLI と AWS Tools for PowerShell のコマンド対応表](#aws-cli-と-aws-tools-for-powershell-のコマンド対応表)
    - [自分のグローバル IP を知りたい、特定の IP アドレスの位置情報とか調べたい](#自分のグローバル-ip-を知りたい特定の-ip-アドレスの位置情報とか調べたい)
        - [ipinfo.io](#ipinfoio)
        - [checkip](#checkip)
    - [GiB, MiB 等の単位変換](#gib-mib-等の単位変換)
    - [CIDR 範囲調べたい](#cidr-範囲調べたい)
    - [OAuth 2.0 を試したい](#oauth-20-を試したい)
    - [OpenID Connect を試したい](#openid-connect-を試したい)
    - [SAML デコードしたい](#saml-デコードしたい)
    - [Weh Authn 試したい](#weh-authn-試したい)
    - [E-ONTAP](#e-ontap)
    - [IPA: Information-technology Promotion Agency, Japan](#ipa-information-technology-promotion-agency-japan)
        - [インターネットセキュリティ小辞典](#インターネットセキュリティ小辞典)
        - [セキュリティ関連 RFC](#セキュリティ関連-rfc)
    - [Linux のメモリ計算](#linux-のメモリ計算)
- [仕様とかリファレンスとか](#仕様とかリファレンスとか)
    - [AWS Guides and API Reference](#aws-guides-and-api-reference)
    - [AWS CLI Reference](#aws-cli-reference)
    - [AWS IAM](#aws-iam)
        - [IAM ID](#iam-id)
        - [Actions, Resources, Condition Keys](#actions-resources-condition-keys)
    - [CloudFormation Reference](#cloudformation-reference)
        - [AWS Resource and Property Types Reference](#aws-resource-and-property-types-reference)
    - [SAM: Serverless Application Model](#sam-serverless-application-model)
        - [AWS Serverless Application Model Template Specification](#aws-serverless-application-model-template-specification)
        - [SAM CLI Command Reference](#sam-cli-command-reference)
    - [API Gateway](#api-gateway)
        - [API Gateway OpenAPI Extensions](#api-gateway-openapi-extensions)
    - [OpenAPI, Swagger](#openapi-swagger)
    - [ウェブ関連仕様 日本語訳](#ウェブ関連仕様-日本語訳)
    - [OpenID Japan 資料](#openid-japan-資料)
    - [HTML Standard](#html-standard)
    - [ECMAScript 2019](#ecmascript-2019)
    - [Markdown](#markdown)
        - [GFM: GitHub Flavored Markdown](#gfm-github-flavored-markdown)
        - [Qiita Markdown Cheat Sheet](#qiita-markdown-cheat-sheet)
    - [GNU](#gnu)
        - [Coreutils](#coreutils)
    - [YAML: Ain't Markup Language](#yaml-aint-markup-language)
    - [JSON: JavaScript Object Notation](#json-javascript-object-notation)
        - [JSON Schema](#json-schema)
    - [NET Core CLI](#net-core-cli)
    - [PostgreSQL](#postgresql)
    - [MySQL](#mysql)

<!-- /TOC -->

# `javascript`

JavaScript リファレンス - JavaScript | MDN  
https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference

JavaScript 言語情報 - JavaScript | MDN  
https://developer.mozilla.org/ja/docs/Web/JavaScript/Language_Resources

付録: JavaScriptチートシート · JavaScript Primer #jsprimer  
https://jsprimer.net/cheetsheet/

とほほのJavaScriptリファレンス  
http://www.tohoho-web.com/js/

JavaScript and HTML DOM Reference  
https://www.w3schools.com/jsref/default.asp

JavaScript documentation — DevDocs  
https://devdocs.io/javascript/

## JSON を pretty print したい

JSON.stringify の第3引数にタブとか指定すれば OK

```js
JSON.stringify(json_data, null, "\t")
JSON.stringify(json_data, null, 4)
```

JSON.stringify() - JavaScript | MDN  
https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify#Parameters

> space Optional
>
>    出力する JSON 文字列に可読性を目的に空白を挿入するために使う String または Number オブジェクト。これが Number のときは空白として使う空白文字の数を示します。この数字は上限が 10 に設定されていて 10 より大きい場合 10 となります。1 より小さい値は空白を使わないことを示します。これが String のときはその文字列（10 文字より長い場合はその最初の 10 文字）が空白として使われます。もしこの引数が提供されない（または null である）場合は、空白は使用されません。

サンプル

```bash
$ node
> const data = {"hoge": 1, "fuga": 2}
undefined
> console.log(data)
{ hoge: 1, fuga: 2 }
undefined
> console.log(JSON.stringify(data, null, "\t"))
{
        "hoge": 1,
        "fuga": 2
}
undefined
> .exit
```

# `python`

3.6.9 Documentation  
https://docs.python.org/ja/3.6/

## `python -m json.tool`: jq が無い環境で json を見やすく表示する

```bash
$ echo '{"json": "obj", "a": "b"}' | python -m json.tool
{
    "json": "obj",
    "a": "b"
}

# キーのアルファベット順にソート
$ echo '{"json": "obj", "a": "b"}' | python -m json.tool --sort-keys
{
    "a": "b",
    "json": "obj"
}

# help
$ python -m json.tool -h
usage: python -m json.tool [-h] [--sort-keys] [infile] [outfile]

A simple command line interface for json module to validate and pretty-print
JSON objects.

positional arguments:
  infile       a JSON file to be validated or pretty-printed
  outfile      write the output of infile to outfile

optional arguments:
  -h, --help   show this help message and exit
  --sort-keys  sort the output of dictionaries alphabetically by key
```

json --- JSON エンコーダおよびデコーダ — Python 3.7.4 ドキュメント  
https://docs.python.org/ja/3/library/json.html#module-json.tool


## `python -m http.server 8000`: http server をサクッと動かす

```bash
python -m http.server 8000
```

1. コマンドラインと環境 — Python 3.7.4 ドキュメント  
https://docs.python.org/ja/3/using/cmdline.html#cmdoption-m

> -m <module-name>
>
>    sys.path から指定されたモジュール名のモジュールを探し、その内容を __main__ モジュールとして実行します。
>
>    引数は module 名なので、拡張子 (.py) を含めてはいけません。モジュール名は有効な Python の絶対モジュール名 (absolute module name) であるべきですが、実装がそれを強制しているとは限りません (例えば、ハイフンを名前に含める事を許可するかもしれません)。

21.22. http.server --- HTTP サーバ — Python 3.6.9 ドキュメント  
https://docs.python.org/ja/3.6/library/http.server.html

> このモジュールは HTTP (web) サーバを実装するためのクラスを提供しています。

21.22. http.server --- HTTP サーバ — Python 3.6.9 ドキュメント  
https://docs.python.org/ja/3.6/library/http.server.html#http.server.SimpleHTTPRequestHandler

> http.server can also be invoked directly using the -m switch of the interpreter with a port number argument. Similar to the previous example, this serves files relative to the current directory:
> 
> python -m http.server 8000
>
> By default, server binds itself to all interfaces. The option -b/--bind specifies a specific address to which it should bind. For example, the following command causes the server to bind to localhost only:
> 
> python -m http.server 8000 --bind 127.0.0.1
> 
> バージョン 3.4 で追加: --bind 引数が導入されました。


# `npm`: Node Package Manager

npm | build amazing things
https://www.npmjs.com/

## `npm` cli

npm/cli: a package manager for JavaScript, report bugs & get support at:
https://github.com/npm/cli

CLI documentation | npm Documentation
https://docs.npmjs.com/cli-documentation/

### `npm init`, `npm install package-name`: 初期セットアップ

```bash
# package.json 作る
npm init

# ローカルにパッケージをインストールする package.json への追記は勝手にやってくれる
npm install aws-sdk
```

### `npm install package-name@xxx`: バージョンを指定してパッケージをインストールする

```bash
$ npm install aws-sdk@2.531.0
```

npm-install | npm Documentation  
https://docs.npmjs.com/cli/install

バージョン指定

> npm install [<@scope>/]<name>@<version>:
> 
> Install the specified version of the package. This will fail if the version has not been published to the registry.
> 
> Example:
> 
>     npm install sax@0.1.1
>     npm install @myorg/privatepackage@1.5.0

バージョンレンジ指定

> npm install [<@scope>/]<name>@<version range>:
> 
> Install a version of the package matching the specified version range. This will follow the same rules for resolving dependencies described in package.json.
> 
> Note that most version ranges must be put in quotes so that your shell will treat it as a single argument.
> 
> Example:
> 
>     npm install sax@">=0.1.0 <0.2.0"
>     npm install @myorg/privatepackage@">=0.1.0 <0.2.0"



## `npx`: execute npm package binaries

npm/npx: npm package executor
https://github.com/npm/npx


# Visual Studio Code

Documentation for Visual Studio Code
https://code.visualstudio.com/docs

Extensions for Visual Studio family of products | Visual Studio Marketplace  
https://marketplace.visualstudio.com/

## Extensions

Managing Extensions in Visual Studio Code  
https://code.visualstudio.com/docs/editor/extension-gallery

### Whitespace+: スペースやタブに色付けしてくれる

Whitespace+ - Visual Studio Marketplace  
https://marketplace.visualstudio.com/items?itemName=davidhouchin.whitespace-plus

スペースを削除してくれるヤツとか色々あるが、Markdown だと改行するのに行末スペース2つ必要で、割とよく使うので色付けしてくれるだけで嬉しい。

### zenkaku: 全角スペースをハイライトしてくれる

zenkaku - Visual Studio Marketplace
https://marketplace.visualstudio.com/items?itemName=mosapride.zenkaku

### Markdown TOC: 日本語使っててもいい感じに TOC を作ってくれる

Auto Markdown TOC が日本語見出しにも対応してて良い感じ

Auto Markdown TOC - Visual Studio Marketplace
https://marketplace.visualstudio.com/items?itemName=huntertran.auto-markdown-toc

## ショートカット

### 一覧

Visual Studio Code Key Bindings
https://code.visualstudio.com/docs/getstarted/keybindings#_keyboard-shortcuts-reference

keyboard-shortcuts-macos.pdf
https://code.visualstudio.com/shortcuts/keyboard-shortcuts-macos.pdf

### `Command + Shift + P`: コマンドパレット

雑に検索してショートカットを実行してくれる

Visual Studio Code User Interface  
https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette

> `⌘P` will let you navigate to any file or symbol by typing its name
> `⌃⇧Tab` will cycle you through the last set of files opened
> `⇧⌘P` will bring you directly to the editor commands
> `⇧⌘O` will let you navigate to a specific symbol in a file
> `⌃G` will let you navigate to a specific line in a file

### `Command + P`: 名前を入力して任意のファイルかシンボルに移動

### `control + Tab`: タブ切り替え

`control + Shift + Tab` で逆順

### `Command + Shift + O`: Markdown の見出しをベースに移動できる。正確にはファイル内のシンボル移動

便利

### `control + G`: 特定行に移動

Mac だと若干押しづらくない？

### `Command + K -> Z`: Zen Mode

Visual Studio Code Tips and Tricks  
https://code.visualstudio.com/docs/getstarted/tips-and-tricks#_zen-mode

`Esc` で解除

### `Command + Shift + [`, `Command + option + right` タブの左右移動


# `docker`

docker | Docker Documentation
https://docs.docker.com/engine/reference/commandline/docker/

## `jshell` をサクッと使いたい

```bash
docker run -it openjdk jshell
```

openjdk - Docker Hub
https://hub.docker.com/_/openjdk

jshell
https://docs.oracle.com/javase/9/tools/jshell.htm

## docker official images

この辺に情報がある。

Official Images on Docker Hub | Docker Documentation
https://docs.docker.com/docker-hub/official_images/

Explore - Docker Hub
https://hub.docker.com/search/?q=&type=image&image_filter=official

official-images/library at master · docker-library/official-images
https://github.com/docker-library/official-images/tree/master/library

docker-library/docs: Documentation for Docker Official Images in docker-library
https://github.com/docker-library/docs

## Apache(httpd) をサクッと動かす

```bash
# フォアグラウンド
docker run -p 8080:80 --name webserver httpd:latest

# バックグラウンド
docker run -p 8080:80 --name webserver -d httpd:latest

# 停止、削除
docker stop webserver
docker rm webserver
```

httpd - Docker Hub
https://hub.docker.com/_/httpd

## nginx をサクッと動かす

```bash
# ポートマッピング
docker run --name some-nginx -d -p 8080:80 nginx:latest

# スタティックコンテンツをホストする
docker run --name some-nginx -p 8080:80 -v /host/content/path:/usr/share/nginx/html:ro -d nginx:latest

# ローカルの conf ファイルを使う
docker run --name some-nginx -v /host/path/nginx.conf:/etc/nginx/nginx.conf:ro -d nginx:latest

# nginx を debug mode で動かす
docker run --name some-nginx -v /host/path/nginx.conf:/etc/nginx/nginx.conf:ro -d nginx nginx-debug -g 'daemon off;'

# 停止、削除
docker stop some-nginx
docker rm some-nginx
```

## MySQL をサクッと動かす

```bash
docker run --name some-mysql -e MYSQL_ROOT_PASSWORD=my-secret-pw -d mysql:latest
docker exec -it some-mysql mysql -u root -p
docker stop some-mysql
docker rm some-mysql
```

mysql - Docker Hub
https://hub.docker.com/_/mysql

## PostgreSQL をサクッと動かす

```bash
docker run --name some-postgres -e POSTGRES_PASSWORD=mysecretpassword -d postgres:latest
docker exec -it some-postgres psql -U postgres
docker stop some-postgres
docker rm some-postgres
```

postgres - Docker Hub
https://hub.docker.com/_/postgres

# `echo`

GNU Coreutils: 15.1 echo: テキストを 1 行表示する  
https://linuxjm.osdn.jp/info/GNU_coreutils/coreutils-ja_105.html#echo-invocation

## `echo -n 'hoge'`: 改行を出力しない

```bash
echo -n 'hoge'
```

## `echo -e 'hoge\nfuga'`: 改行を出力する

```bash
echo -e 'hoge\nfuga'
```

# `say`: テキスト読み上げ

Mac でとりあえず音出るか確かめたい時など

```bash
say hello
```

say Man Page - macOS - SS64.com
https://ss64.com/osx/say.html

# `grep`: ファイルのパターンサーチ

Man page of GREP  
https://linuxjm.osdn.jp/html/GNU_grep/man1/grep.1.html

grep  
https://www.freebsd.org/cgi/man.cgi?query=grep

## `grep -c hoge`: マッチした行カウント

`-c`, `--count`

```bash
echo -e 'a\nb\nc\nd' | grep a -c
1
```

カウントの `c`

## `grep -c -v hoge`: マッチしなかった行カウント

`-v`, `--invert-match`

```bash
echo -e 'a\nb\nc\nd' | grep -v -c a
3
```

インバートの `v`

# `wc`

## `echo -e '1\n2\n3' | wc -l`: 行数をカウントしたい

```bash
echo -e '1\n2\n3' | wc -l
       3
```

## `pbpaste | wc -w`: クリップボードにコピーした文字列の長さを知りたい

```bash
pbpaste | wc -w
```

wc
https://www.freebsd.org/cgi/man.cgi?wc

> -c	The number of bytes in each input file is written to the standard output.  This will cancel out any prior usage of the -m option.

> -m	The number of characters in each input file is written to the standard output. If the current locale does not support multi-byte characters, this is equivalent to the	-c option.  This will cancel out any prior usage of the -c option.

パッと見、 `-c` でも良さそうな感じがしますが、 `-c` オプションは文字列の長さではなくてバイト数  
`-m` でも current locale がマルチバイト文字をサポートしてない場合は `-c` と同等になるとありますが、気にする機会はあまり無さそう

```bash
# 'あああ' をクリップボードにコピーすると・・・
echo -n あああ | pbcopy

# -m だと文字列の長さとして 3 を返す
pbpaste | wc -m
       3

# -c だとバイト数として 3 を返す
pbpaste | wc -c
       9
```

# `cut`: 受け取った文字列を分割して扱いたい

```bash
# デフォルトでタブを delimiter として扱う。 
# -f は fields, 区切った文字の何番目の文字を出力するか。
echo -e "hoge\tfuga" | cut -f 2
fuga

# delimiter を変更したい場合 -d で指定
echo 'hogehoge_fugafuga' | cut -d _ -f 2
fugafuga
```

Linux と BSD で微妙に違うので注意。
Linux の場合 [Textutils](https://www.gnu.org/software/textutils/textutils.html) というパッケージに含まれていたが、その後 Coreutils に統合されたらしい。

cut
https://www.freebsd.org/cgi/man.cgi?cut

Man page of CUT
https://linuxjm.osdn.jp/html/GNU_coreutils/man1/cut.1.html

# 圧縮, 展開

## zip

Zip (file format) - Wikipedia  
https://en.wikipedia.org/wiki/Zip_(file_format)

APPNOTE.TXT  
https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT

ISO - ISO/IEC 21320-1:2015 - Information technology -- Document Container File -- Part 1: Core  
https://www.iso.org/standard/60101.html

zip(1): package/compress files - Linux man page  
https://linux.die.net/man/1/zip

zip  
https://www.freebsd.org/cgi/man.cgi?query=zip

### `zip archived.zip hoge.txt`: ファイル圧縮

```bash
zip archived.zip hoge.txt
  adding: hoge.txt (stored 0%)
```

### `zip -r archived.zip ./hogedir`: ディレクトリ圧縮

```bash
tree hogedir/
hogedir/
├── 1.txt
└── 2.txt

0 directories, 2 files

zip -r archived.zip ./hogedir/
  adding: hogedir/ (stored 0%)
  adding: hogedir/2.txt (stored 0%)
  adding: hogedir/1.txt (stored 0%)
```

### `zipinfo archived.zip`: 圧縮ファイルの情報を見る

```bash
zipinfo archived.zip 
Archive:  archived.zip
Zip file size: 618 bytes, number of entries: 4
-rw-r--r--  3.0 unx        0 bx stor 19-Sep-06 14:05 hoge.txt
drwxr-xr-x  3.0 unx        0 bx stor 19-Sep-06 14:06 hogedir/
-rw-r--r--  3.0 unx        0 bx stor 19-Sep-06 14:06 hogedir/2.txt
-rw-r--r--  3.0 unx        0 bx stor 19-Sep-06 14:06 hogedir/1.txt
4 files, 0 bytes uncompressed, 0 bytes compressed:  0.0%
```

## `unzip archived.zip`: 圧縮ファイルの展開

unzip(1) - Linux man page  
https://linux.die.net/man/1/unzip

unzip(1)  
https://www.freebsd.org/cgi/man.cgi?query=unzip

```bash
unzip archived.zip
Archive:  archived.zip
replace hoge.txt? [y]es, [n]o, [A]ll, [N]one, [r]ename: A
 extracting: hoge.txt                
 extracting: hogedir/2.txt           
 extracting: hogedir/1.txt 
```

# パフォーマンス系

## CPU 使用率を上げたい

```bash
yes > /dev/null &
```

# Git

Git - Reference  
https://git-scm.com/docs

## `.gitignore` あれこれ

Git - gitignore Documentation  
https://git-scm.com/docs/gitignore

[Git] .gitignoreの仕様詳解 - Qiita  
https://qiita.com/anqooqie/items/110957797b3d5280c44f

気付いたら.gitignoreはgiboで自動生成する時代になっていた - Qiita  
https://qiita.com/tmknom/items/c4bcebe17d25381fa45d

simonwhitaker/gibo: Easy access to gitignore boilerplates  
https://github.com/simonwhitaker/gibo

## `git rm filename`: Git で管理しているファイルを削除したい

```bash
# ファイル指定
git rm filename

# ディレクトリ
git rm -r /path/to/dir
```

Git - git-rm Documentation  
https://git-scm.com/docs/git-rm

> DESCRIPTION
> 
> Remove files from the index, or from the working tree and the index. git rm will not remove a file from just your working directory. (There is no option to remove a file only from the working tree and yet keep it in the index; use /bin/rm if you want to do that.) The files being removed have to be identical to the tip of the branch, and no updates to their contents can be staged in the index, though that default behavior can be overridden with the -f option. When --cached is given, the staged content has to match either the tip of the branch or the file on disk, allowing the file to be removed from just the index.

> -r
>     Allow recursive removal when a leading directory name is given.

## `git rm --cached filename`: 特定ファイルを削除せずに Git 管理から外したい

`.gitignore` 作るの忘れて commit してしまった場合など

```bash
# ファイル指定
git rm --cached filename

# ディレクトリ
git rm -r --cached /path/to/dir
```

Git - git-rm Documentation  
https://git-scm.com/docs/git-rm

> DESCRIPTION
> 
> Remove files from the index, or from the working tree and the index. git rm will not remove a file from just your working directory. (There is no option to remove a file only from the working tree and yet keep it in the index; use /bin/rm if you want to do that.) The files being removed have to be identical to the tip of the branch, and no updates to their contents can be staged in the index, though that default behavior can be overridden with the -f option. When --cached is given, the staged content has to match either the tip of the branch or the file on disk, allowing the file to be removed from just the index.

> -r
>     Allow recursive removal when a leading directory name is given.

> --cached
>     Use this option to unstage and remove paths only from the index. Working tree files, whether modified or not, will be left alone.



## `git log -1`, `git log -n 1`: 直前の commit log を見たい

git account 間違ってないかチェックするのに使う

```bash
git log -1
```

Git - git-log Documentation  
https://git-scm.com/docs/git-log#Documentation/git-log.txt--ltnumbergt

> -<number>
> -n <number> 

## `git diff --cached filename`: add したファイルの diff が見たい

```bash
git add README.md
git diff --cached README.md
```

Git - git-diff Documentation  
https://git-scm.com/docs/git-diff#Documentation/git-diff.txt-emgitdiffemltoptionsgt--cachedltcommitgt--ltpathgt82308203

> git diff [<options>] --cached [<commit>] [--] [<path>…​]
> 
>     This form is to view the changes you staged for the next commit relative to the named <commit>. Typically you would want comparison with the latest commit, so if you do not give <commit>, it defaults to HEAD. If HEAD does not exist (e.g. unborn branches) and <commit> is not given, it shows all staged changes. --staged is a synonym of --cached.

## ローカルでトピックブランチ作ってマージして消す

```bash
# -b で新規ブランチ作成してブランチ切り替え
git checkout -b topic-name

# 適当に commit 
git add hoge
git commit -m hoge

# 元のブランチに戻してマージしてプッシュ
git checkout master
git merge topic-name
git push origin master

# トピックブランチ削除
git branch -d topic-name
```

## `git commit --amend -m 'fix message'`: 直前の commit メッセージ変更

```bash
git commit --amend -m 'fix message'
```

Git - git-commit Documentation  
https://git-scm.com/docs/git-commit#Documentation/git-commit.txt---amend

## 直前の commit 取り消し

```bash
git reset --soft HEAD^
```

Git - git-reset Documentation
https://git-scm.com/docs/git-reset

## ファイルやディレクトリのリネーム

`git mv` 使わずに `mv` コマンドで変更すると、 `git rm old-name.txt`, `git add new-name.txt` する必要が生じて面倒 

```bash
git mv old-name.txt new-name.txt
```

Git - git-mv Documentation
https://git-scm.com/docs/git-mv

## プライベートな GitHub アカウントで使ってる Git ユーザーを設定する

対象プロジェクトのディレクトリで設定する

```bash
git config --local user.name itooww
git config --local user.email xxxxxxx+itooww@users.noreply.github.com
git config --list --local
```

`user.email` に設定するメアドは https://github.com/settings/emails を確認する。

# AWS CLI

## `aws configure --profile hoge`: profile 追加

configure — AWS CLI 1.16.234 Command Reference  
https://docs.aws.amazon.com/cli/latest/reference/configure/index.html

```bash
aws configure --profile hoge
```

## AWS CLI で IAM Role のクレデンシャルを使う

AWS CLI での IAM ロールの使用 - AWS Command Line Interface  
https://docs.aws.amazon.com/ja_jp/cli/latest/userguide/cli-configure-role.html

`~/.aws/credentials` に下記のようなフォーマットで設定を追記

```
[profile roleprofile]
role_arn = arn:aws:iam::123456789012:role/sample-role
credential_source = assume role 元の profile name
```

あとは IAM Role の信頼関係で AssumeRole を許可すれば使える。

```bash
aws ec2 describe-regions --profile roleprofile
```

## Pinpoint

pinpoint — AWS CLI 1.16.246 Command Reference  
https://docs.aws.amazon.com/cli/latest/reference/pinpoint/index.html

### `update-endpoint`: エンドポイントの登録、更新

```bash
REGION=us-east-1
APPLICATION_ID=xxx
ENDPOINT_ID=yyy
ADDRESS=sample@example.com
CHANNEL_TYPE=EMAIL
aws --region $REGION pinpoint update-endpoint --application-id $APPLICATION_ID --endpoint-id $ENDPOINT_ID --endpoint-request Address=$ADDRESS,ChannelType=$CHANNEL_TYPE
```

update-endpoint — AWS CLI 1.16.246 Command Reference  
https://docs.aws.amazon.com/cli/latest/reference/pinpoint/update-endpoint.html

### `get-entpoid`: エンドポイント取得

```bash
REGION=us-east-1
APPLICATION_ID=2b46eda229614d9a9933f6df13efb341
ENDPOINT_ID=xxx
aws --region $REGION pinpoint get-endpoint --application-id $APPLICATION_ID --endpoint-id $ENDPOINT_ID
```

get-endpoint — AWS CLI 1.16.246 Command Reference  
https://docs.aws.amazon.com/cli/latest/reference/pinpoint/get-endpoint.html

## ECS/Fargate

### `run-task`: タスク実行

run-task  
https://docs.aws.amazon.com/cli/latest/reference/ecs/run-task.html

#### Fargage

```bash
CLUSTER_NAME=fargate-cluster-name
TASK_DEFINITION=fargate-definition-name:1
SUBNET=subnet-xxx
SECURITY_GROUP=sg-xxx

# とりあえず動かす
aws ecs run-task --cluster $CLUSTER_NAME --task-definition $TASK_DEFINITION --count 1 --launch-type FARGATE --network-configuration "awsvpcConfiguration={subnets=[$SUBNET],securityGroups=[$SECURITY_GROUP],assignPublicIp=ENABLED}"


# コマンド上書き
CONTAINER_NAME=container-name
COMMAND="[\"echo\", \"hoge\"]"
aws ecs run-task --cluster $CLUSTER_NAME --task-definition $TASK_DEFINITION --overrides "{\"containerOverrides\":[{\"name\":\"$CONTAINER_NAME\",\"command\":$COMMAND}]}" --count 1 --launch-type FARGATE --network-configuration "awsvpcConfiguration={subnets=[$SUBNET],securityGroups=[$SECURITY_GROUP],assignPublicIp=ENABLED}"
```

#### EC2

```bash
CLUSTER_NAME=ec2-cluster-name
TASK_DEFINITION=ec2-definition-name:1


# とりあえず動かす
aws ecs run-task --cluster $CLUSTER_NAME --task-definition $TASK_DEFINITION --count 1

# コマンド上書き
CONTAINER_NAME=container-name
COMMAND="[\"echo\", \"hoge\"]"

aws ecs run-task --cluster $CLUSTER_NAME --task-definition $TASK_DEFINITION --overrides "{\"containerOverrides\":[{\"name\":\"$CONTAINER_NAME\",\"command\":$COMMAND}]}"' --count 1
```

## Systems Manager

### `put-parameter`: パラメーターストアに値を登録、更新

```bash
aws ssm put-parameter --name myParam --value hogehoge --type String

# 更新時には --overwrite オプションが必要
aws ssm put-parameter --name myParam --value hogehogev2 --type String --overwrite

# KMS で暗号化する場合, --type を SecureString にする
aws ssm put-parameter --name mySecureParam --value hogehoge --type SecureString
aws ssm put-parameter --name mySecureParam --value hogehogev2 --type SecureString --overwrite
```

put-parameter — AWS CLI 1.16.223 Command Reference
https://docs.aws.amazon.com/cli/latest/reference/ssm/put-parameter.html

### `get-parameter`: パラメーターストアの値を取得

```bash
aws ssm get-parameter --name myParam 

# 実際の Value だけ取得する
aws ssm get-parameter --name myParam --query 'Parameter.Value' --output text

# SecureString の場合、複合のために --with-decryption が必要。
# --with-decryption を指定しなくてもエラーにはならないが、 Value が暗号化されているので別途複合が必要になる
aws ssm get-parameter --name mySecureParam --with-decryption
aws ssm get-parameter --name mySecureParam --with-decryption --query 'Parameter.Value' --output text
```

get-parameter — AWS CLI 1.16.223 Command Reference
https://docs.aws.amazon.com/cli/latest/reference/ssm/get-parameter.html


## Step Functions

### `create-state-machine`: ステートマシーン作成

state machine の定義は別途 json ファイルで作っておく。

```bash
aws stepfunctions create-state-machine --name mystatemachine --definition file://state-machine-definition.json --role-arn "arn:aws:iam::123456789012:role/service-role/StatesExecutionRole-ap-northeast-1"
```

create-state-machine — AWS CLI 1.16.216 Command Reference
https://docs.aws.amazon.com/cli/latest/reference/stepfunctions/create-state-machine.html

### `start-execution`: ステートマシーン実行

state machine への入力は別途 json ファイルで作っておく。

```bash
aws stepfunctions start-execution --state-machine-arn arn:aws:states:ap-northeast-1:123456789012:stateMachine:foo --input file://input.json
```

start-execution — AWS CLI 1.16.216 Command Reference
https://docs.aws.amazon.com/cli/latest/reference/stepfunctions/start-execution.html

## CloudFormation

### `validate-template`: template 検証

指定した cloudformation template のシンタックスに問題が無いかチェックしてくれる。
シンタックスに問題なくても、スタック作成時には他の様々な理由によってエラーが発生する場合があるので注意。

```bash
aws cloudformation validate-template --template-body file://./mytemplate.yaml
```

validate-template — AWS CLI 1.16.216 Command Reference
https://docs.aws.amazon.com/cli/latest/reference/cloudformation/validate-template.html


### `deploy`: template を使ってデプロイ

`deploy` コマンドは `create-stack`, 'create-change-set', 'execute-change-set' といったコマンドを内包しているので新規作成であろうと更新であろうとコレ一発。

```bash
aws cloudformation deploy --template-file ./mytemplate.yaml --stack-name mystack

# template で parameter 使う場合
aws cloudformation deploy --template-file ./mytemplate.yaml --stack-name mystack --parameter-overrides MyParameter1st=hoge MyParameter2nd=fuga
```

deploy — AWS CLI 1.16.171 Command Reference
https://docs.aws.amazon.com/cli/latest/reference/cloudformation/deploy/index.html


### `describe-stack-events`: スタックのイベント取得

作成したスタックのイベントを取得

```bash
aws cloudformation describe-stack-events --stack-name mystack
```

describe-stack-events — AWS CLI 1.16.171 Command Reference
https://docs.aws.amazon.com/cli/latest/reference/cloudformation/describe-stack-events.html


### `describe-stack-resources`: スタックのリソース取得

スタックで作成されたリソースを取得

```bash
aws cloudformation describe-stack-resources --stack-name mystack
```

describe-stack-resources — AWS CLI 1.16.171 Command Reference
https://docs.aws.amazon.com/cli/latest/reference/cloudformation/describe-stack-resources.html

### `describe-stacks`: スタック情報取得

Outputs の値を取りたい時に使う

```bash
aws cloudformation describe-stacks --stack-name mystack
```

同名スタックが複数存在しない前提だが、`--query` を使って Outputs だけ抽出するコマンド

```
aws cloudformation describe-stacks --stack-name mystack --query 'Stacks[0].Outputs'
```

より具体的に、Outputs で実行するコマンドを生成してて、Mac からそのままコピーして実行したい場合、↓ みたいな感じで使える。

```
aws cloudformation describe-stacks --stack-name mystack --query 'Stacks[0].Outputs[0].OutputValue' --output text | pbcopy
# Ctrl + V, Enter
```


### `delete-stack`: スタック削除。

`DeletionPolicy: Retain` とか指定しているリソースがあると削除漏れが発生するので注意

```bash
aws cloudformation delete-stack --stack-name mystack
```

delete-stack — AWS CLI 1.16.171 Command Reference
https://docs.aws.amazon.com/cli/latest/reference/cloudformation/delete-stack.html

DeletionPolicy 属性 - AWS CloudFormation
https://docs.aws.amazon.com/ja_jp/AWSCloudFormation/latest/UserGuide/aws-attribute-deletionpolicy.html

# AWS Chalice

aws/chalice: Python Serverless Microframework for AWS  
https://github.com/aws/chalice

AWS Chalice — Python Serverless Microframework for AWS 1.11.0 documentation  
https://chalice.readthedocs.io/en/latest/

AWS Chalice Workshop — AWS Chalice Workshop 0.0.1 documentation  
https://chalice-workshop.readthedocs.io/en/latest/index.html

# ランダム文字列生成

```bash
head -c 1m /dev/urandom | base64
```

head の -c オプション(byte 指定)で大きさは調整すれば OK

# pandoc を使って markdown を XWiki 記法に変換

```bash
pandoc -f markdown -t xwiki -o converted.wiki original.md 
```

`-f`: from
`-t`: to
`-o`: output

## 参考

Pandoc - Pandoc User’s Guide
https://pandoc.org/MANUAL.html

# `curl`

## 通信の詳細を見たい

`-v` オプションを使う

```bash
curl -v https://www.example.com/
```

## レスポンスされるステータスコードを見たい

`-I` オプションを使う

```bash
curl -I https://www.example.com/
```

**`-I` 使うと HEAD メソッドでのリクエストになる。**
GET, POST 等の他メソッドを使いたい場合には `curl -I -X GET https://www.example.com/` のようにメソッドの指定が必要になるので注意

## POST したい

```bash
curl https://www.example.com/ -X POST -d 'Authorization: xxx' -d 'query: yyy'
```

## リクエストをしばらく連続して行いたい

`while` を使う

```bash
while sleep 1s; do curl -s https://www.example.com/; done
```

`watch` を使う方法もあるが、履歴を追ったりしたい場合が多いので `while` を使うことが多い

```bash
watch curl -s https://www.example.com/
```

`curl` じゃないけど、`httping` という便利なツールがある。
https://www.vanheusden.com/httping/
https://github.com/flok99/httping

```bash
httping --url https://www.example.com/hogeaaa -s
Auto enabling SSL due to https-URL
PING www.example.com:443 (/hogeaaa):
connected to 93.184.216.34:443 (269 bytes), seq=0 time=545.77 ms 404 Not Found
connected to 93.184.216.34:443 (269 bytes), seq=1 time=604.96 ms 404 Not Found
connected to 93.184.216.34:443 (269 bytes), seq=2 time=569.02 ms 404 Not Found
^CGot signal 2
--- https://www.example.com/hogeaaa ping statistics ---
3 connects, 0 ok, 100.00% failed, time 4038ms
```

ステータスコードが知りたいので `-s` を付けると良さげ。

デプロイ動作の検証とかに便利。

## 参考

curl - How To Use
https://curl.haxx.se/docs/manpage.html

# `nc`

## HTTP リクエスト

```bash
$ nc example.com 80
GET / HTTP/1.1
Host:example.com
# ENTER
```

## サーバーとして待ち受ける、HTTP リクエストをタイムアウトさせたい

HTTP のリクエストヘッダー確認したい時に便利

```bash
nc -kvl 80
```

以下のような curl コマンドでタイムアウト

```bash
curl http://localhost -m 5
```

`-m` は `--max-time` で curl が始まってからのタイムアウト設定。単位は秒。
`--connect-timeout` という設定もできるが、これはサーバーに接続するまでのタイムアウトなので、`nc` で受けている場合には必要ない。(`nc` がリクエストを受け付けるものの、レスポンスは返さないという挙動になる)

## ポート状況の確認

やんごとなき事情がある場合に使う。
広範囲のスキャンはしてはいけない。

```bash
nc -vz www.example.com 80-80
```

## 参考

nc(1): arbitrary TCP/UDP connections/listens - Linux man page
https://linux.die.net/man/1/nc

nc(netcat)コマンドで覚えておきたい使い方8個 | 俺的備忘録 〜なんかいろいろ〜
https://orebibou.com/2015/11/ncnetcat%E3%82%B3%E3%83%9E%E3%83%B3%E3%83%89%E3%81%A7%E8%A6%9A%E3%81%88%E3%81%A6%E3%81%8A%E3%81%8D%E3%81%9F%E3%81%84%E4%BD%BF%E3%81%84%E6%96%B98%E5%80%8B/

curl備忘録 - Qiita
https://qiita.com/hijili/items/63a7ed4885974810e036

# `openssl`

## サーバーに設定されている証明書の確認

```bash
echo "Q" | openssl s_client -connect www.example.com:443 -showcerts
```

### SNI

```bash
echo "Q" | openssl s_client -connect www.example.com:443 -servername hoge.example.com -showcerts
```

## HTTP リクエスト

```bash
$ openssl s_client -connect example.com:443
# 証明書情報
GET / HTTP/1.1
Host:example.com
# ENTER
```

## 参考

/docs/man1.0.2/apps/openssl.html
https://www.openssl.org/docs/man1.0.2/apps/openssl.html

opensslでサーバ証明書を取得するワンライナー - Qiita
https://qiita.com/RadicalFunction/items/e2f97306778281bacafc

# `date`

ログとかトークンの時刻を確認したい場合に便利。
Mac の date コマンド前提のオプションなので注意。Linux の date コマンドはオプションが異なる。


## unixtime を JST に変換

`-r` オプションを使う

```bash
date -r 1548754204
2019年 1月29日 火曜日 18時30分04秒 JST
```

## unixtime を UTC に変換

`-r`, `-u` オプションを使う。

```bash
date -r 1548754204 -u
2019年 1月29日 火曜日 09時30分04秒 UTC
```

`-u` は UTC 

## 現在時刻を unixtime で出力

```bash
$ date +%s
1561973903
```

## 現在時刻を ISO 8601 で出力

### JST

```bash
$ date +%FT%TZ
2019-07-01T18:35:08Z
```

### UTC

```bash
$ date -u +%FT%TZ
2019-07-01T09:36:47Z
```

## 参考

mac と linux でオプションが異なるので注意

date Man Page - macOS - SS64.com
https://ss64.com/osx/date.html

date(1): print/set system date/time - Linux man page
https://linux.die.net/man/1/date

# XML を jq 的に整形したい

`tidy` コマンドを使う

```bash
$ tidy --indent-cdata true -xml -utf8 -i target.xml
```

## 参考

tidyコマンドでXMLインデント整形する - それマグで！
http://takuya-1st.hatenablog.jp/entry/20110830/1314704820

macでxmlを整形する | ハックノート
https://hacknote.jp/archives/9219/

tidy(1) - Linux man page
https://linux.die.net/man/1/tidy

Tidy Documentation
http://www.html-tidy.org/documentation/

# 環境変数一覧を表示したい

`printenv` コマンドを使えば OK

```bash
$ printenv
```

Man page of printenv
https://linuxjm.osdn.jp/html/gnumaniak/man1/printenv.1.html

# bash

## `while`

```bash
 while sleep 1; do date; done
```

## `for`

```bash
$ for i in {1..5}; do echo $i; done
$ for ( ; ; ); do date; done
```

## 交互にコマンドを実行するスクリプト

alternately-commands-executor.sh

```sh
#!/bin/sh
SLEEP_INTERVAL=1

for i in {1..10}; do
    sleep $SLEEP_INTERVAL;
    echo $i
    if [ $(($i % 2)) -eq 0 ]; then
        date
        echo hoge
    else
        date
        echo fuga
    fi
done
```

実行

```bash
chmod 755 ./alternately-commands-executor.sh
./alternately-commands-executor.sh
```

# 英語

## 苦情とかのクレーム: complaint

complaintの意味・使い方・読み方 | Weblio英和辞書  
https://ejje.weblio.jp/content/complaint

> Make a complaint
> クレームを言う

> I received a complaint.
> 私は、苦情を受けとった

## appearance: 外観

IntelliJ の外観設定とかで使われている

Appearance - Help | IntelliJ IDEA  
https://www.jetbrains.com/help/idea/settings-appearance.html

> Use this page to change the overall look and feel of your IDE.

appearanceの意味・使い方・読み方 | Weblio英和辞書  
https://ejje.weblio.jp/content/appearance

> 主な意味
> 	出現(すること)、(会などに)姿を見せること、出席、出演、出場、出頭、出廷、(書物の)出版、発刊、(記事の)掲載

## 分かりにくくてスマヌ: `Sorry it's hard to understand.`, `Please excuse my lack of explanation.`

Weblio和英辞書 -「わかりにくくてごめんなさい」の英語・英語例文・英語表現  
https://ejje.weblio.jp/content/%E3%82%8F%E3%81%8B%E3%82%8A%E3%81%AB%E3%81%8F%E3%81%8F%E3%81%A6%E3%81%94%E3%82%81%E3%82%93%E3%81%AA%E3%81%95%E3%81%84

説明不足でごめんなさいって英語でなんて言うの？ - DMM英会話なんてuKnow?  
https://eikaiwa.dmm.com/uknow/questions/3917/

## なんか追加で情報必要なら声かけて: If you need additional information, please let me know.

簡単1分！ネイティブ表現トレーニング　ビジネス英語編 - 英語のまぐまぐ！ | 英語のまぐ！  
https://english.mag2.com/qa_business/57.html

Let me know if you need any additional information.の意味・使い方 - 英和辞典 WEBLIO辞書  
https://ejje.weblio.jp/content/Let+me+know+if+you+need+any+additional+information.

## 再発、再現: recurrent

recurrent とは 意味・読み方・表現 | Weblio英和辞書  
https://ejje.weblio.jp/content/recurrent

イシューが再発している  
The issue has recurrent

# 気になったブログ記事など

## Ｃプログラミング診断室

Ｃプログラミング診断室  
http://www.pro.or.jp/~fuji/mybooks/cdiag/

## AWS X-Ray SDK for the Python のローカルサンプリングルール読み込んでいる箇所の実装

aws/aws-xray-sdk-python: AWS X-Ray SDK for the Python programming language  
https://github.com/aws/aws-xray-sdk-python

aws-xray-sdk · PyPI  
https://pypi.org/project/aws-xray-sdk/

aws-xray-sdk-python/sampler.py at 17dc8759e61157c55b846515581e65bad29d8940 · aws/aws-xray-sdk-python  
https://github.com/aws/aws-xray-sdk-python/blob/17dc8759e61157c55b846515581e65bad29d8940/aws_xray_sdk/core/sampling/local/sampler.py

aws-xray-sdk-python/sampling_rule.py at 17dc8759e61157c55b846515581e65bad29d8940 · aws/aws-xray-sdk-python  
https://github.com/aws/aws-xray-sdk-python/blob/17dc8759e61157c55b846515581e65bad29d8940/aws_xray_sdk/core/sampling/local/sampling_rule.py

`xray_recorder.configure` で json ファイルを読み込ませることもできるし、 Python の dict オブジェクトで指定することも出来るっぽい 

X-Ray SDK for Python の設定 - AWS X-Ray  
https://docs.aws.amazon.com/ja_jp/xray/latest/devguide/xray-sdk-python-configuration.html

サーバーレス環境にデプロイされたウェブフレームワークの計測 - AWS X-Ray  
https://docs.aws.amazon.com/ja_jp/xray/latest/devguide/xray-sdk-python-serverless.html

## MDN まとめ

フロントエンドエンジニア御用達の MDN web docs を網羅した - Qiita  
https://qiita.com/snakada/items/07347d6ad10ae661fbc6

## OAuth の Implicit grant と Authorization code grant について

OAuth 2.0 の Implicit grant 終了のお知らせ - r-weblife  
https://ritou.hatenablog.com/entry/2018/11/12/110613

OAuth 2.0 Implicit Flowをユーザー認証に利用する際のリスクと対策方法について #idcon - r-weblife  
https://ritou.hatenablog.com/entry/20120206/1328484575  

RFC7636として発行されたOAuth PKCEとは - r-weblife  
https://ritou.hatenablog.com/entry/20151018/1445181974

OAuth 2.0 / OpenID Connectにおけるstate, nonce, PKCEの限界を意識する - r-weblife  
https://ritou.hatenablog.com/entry/2019/07/08/070000

## `0.0.0.0` と `127.0.0.1` と `localhot`

0.0.0.0にはアクセスしないこと - Qiita  
https://qiita.com/amuyikam/items/0063df223aed40193ba9

> まとめ  
>     Webサーバでよく見る0.0.0.0はこのホストのすべてのインターフェースでLISTENするという意味  
>     宛先0.0.0.0は無効なアドレスなので、何も考えずにブラウザに0.0.0.0:8000のように入れるのは誤り  
>     ただしOSによっては0.0.0.0を127.0.0.1にルーティングしていることがあるため表面上は問題ないように見える(CORSには引っかかるので混同していると痛い目見るかも)  

# 便利な Web サイト

## プログラミング言語やフレームワークやツールのリファレンスまとめサイト

DevDocs API Documentation  
https://devdocs.io/

## OAuth 2.0, OpenID Connect の技術情報

Authlete  
https://www.authlete.com/ja/developers/

OAuth および OpenID Connect — Authlete ナレッジベース (Beta)  
https://kb.authlete.com/ja/s/oauth-and-openid-connect

## ランダムな JWK (JSON Web Key) を生成できるサイト

mkjwk - JSON Web Key Generator  
https://mkjwk.org/

## AI 生成の顔写真

100,000 AI-Generated Faces – Free to use!
https://generated.photos/

## AWS のセキュリティを学べるサイト

flAWS  
http://flaws.cloud/

## JavaScript チートシート

付録: JavaScriptチートシート · JavaScript Primer #jsprimer  
https://jsprimer.net/cheetsheet/

## 迷路生成アルゴリズムのサンプル

Maze Algorithms  
https://www.jamisbuck.org/mazes/

## AWS, GCP, Azure 等のアイコンを使って構成図を作成できるサイト

Online Diagram and Flowchart Software | Cacoo  
https://cacoo.com/

## AWS の構成図を作成できるサイト

Cloudcraft – Draw AWS diagrams  
https://cloudcraft.co/

## AWS を図でまとめているサイト

Jerry Hargrove  
https://www.awsgeek.com/

## AWS のサービスリリース履歴を管理しているサイト

Jerry Hargrove | History of Amazon Web Services  
https://www.awsgeek.com/pages/AWS-History/

AwsGeek/aws-history  
https://github.com/AwsGeek/aws-history

## EC2, RDS の Instance 早見表

Amazon EC2 Instance Comparison  
https://ec2instances.info/

powdahound/ec2instances.info: Amazon EC2 instance comparison site  
https://github.com/powdahound/ec2instances.info/

## AWS CLI と AWS Tools for PowerShell のコマンド対応表

AWS CLI -eq PowerShell  
https://aws-cli-eq-pwsh.shibata.tech/

stknohg/aws-cli-eq-pwsh: AWS CLI -eq PowerShell  
https://github.com/stknohg/aws-cli-eq-pwsh/

## 自分のグローバル IP を知りたい、特定の IP アドレスの位置情報とか調べたい

### ipinfo.io

IP Address API and Data Solutions - geolocation, company, carrier info, type and more - IPinfo IP Address Geolocation API
https://ipinfo.io/

curl から使えて便利

```bash
$ curl -s ipinfo.io | jq
```

特定の IP 情報も調べられて便利

```bash
$ curl -s ipinfo.io/8.8.8.8 | jq
{
  "ip": "8.8.8.8",
  "hostname": "google-public-dns-a.google.com",
  "city": "Mountain View",
  "region": "California",
  "country": "US",
  "loc": "37.3860,-122.0840",
  "postal": "94035",
  "phone": "650",
  "org": "AS15169 Google LLC"
}
```

### checkip

http://checkip.amazonaws.com/

シンプル。

```bash
$ curl http://checkip.amazonaws.com/
72.21.198.67
```

## GiB, MiB 等の単位変換

Data Storage Conversion Calculator
http://extraconversion.com/data-storage

## CIDR 範囲調べたい

Online IP CIDR / VLSM Supernet Calculator
http://www.subnet-calculator.com/cidr.php

## OAuth 2.0 を試したい

OAuth 2.0 Playground  
https://www.oauth.com/playground/

OAuth 2.0 Playground  
https://developers.google.com/oauthplayground/

## OpenID Connect を試したい

OpenID Connect Playground  
https://openidconnect.net/

Okta OpenID Connect Fun!  
https://okta-oidc-fun.herokuapp.com/continue

oktadeveloper/okta-oidc-flows-example  
https://github.com/oktadeveloper/okta-oidc-flows-example#okta-openid-connect-fun

## SAML デコードしたい

SAML Token - samltool.io  
https://samltool.io/

## Weh Authn 試したい

Yubico demo website  
https://demo.yubico.com/webauthn

Web Authentication Playground  
https://dist-yycvxvsyvu.now.sh/tutorial

## E-ONTAP

Welcome to the E-ONTAP  
https://www.e-ontap.com/

DNS Study  
https://www.e-ontap.com/dns/

DNS 温泉 5 (2018) (5)  
https://www.e-ontap.com/dns/onsen5/#(5)

> DNSの学び方
> 
>     ネット? 本? ほとんどでたらめか不十分
>     実環境から学ぶ? 実装も運用もバラバラでほとんど間違ってます。
>     何を頼れば? RFC しか拠り所はありません。(それも怪しいのに他は如何や)
>     RFC 難しい? はい。読んでも冗長、難解、不正確です。
>     どうすれば? 実装を触りつつ RFC を解釈していきましょう。
>     独学できる? 無理です。DNS 温泉で学ぶ仲間をつくりましょう。
>     今回の DNS 温泉は超初心者向けと聴いたけれど難しくない?
>     難しいです。これから山を登ろうという人に山を見せないでどうしますか。
>     (それでも裾野のごく一部ですが簡単そうな絵本を見せるだけよりはまし)
>     最初から全部理解しようとする必要はないし、それは無理です。
>     わかった気になるのが危ない。私もわからないことだらけです。 

## IPA: Information-technology Promotion Agency, Japan

### インターネットセキュリティ小辞典

Internet Security Glossary  
https://www.ipa.go.jp/security/rfc/RFC2828-00JA.html


### セキュリティ関連 RFC

セキュリティ関連 RFC：IPA 独立行政法人 情報処理推進機構  
https://www.ipa.go.jp/security/rfc/RFC.html


## Linux のメモリ計算

【RHEL】linuxメモリのfreeとmeminfoの関係を図解し利用率の計算方法を説明してみる - のぴぴのメモ  
http://nopipi.hatenablog.com/entry/2015/09/13/181026

# 仕様とかリファレンスとか

## AWS Guides and API Reference

AWS Documentation
https://docs.aws.amazon.com/

サービスのユーザーガイドとか、開発者ガイドとか、API リファレンスとか、チュートリアルとか。

## AWS CLI Reference

AWS CLI Command Reference
https://docs.aws.amazon.com/cli/latest/index.html

## AWS IAM

### IAM ID

IAM ID - AWS Identity and Access Management  
https://docs.aws.amazon.com/ja_jp/IAM/latest/UserGuide/reference_identifiers.html

### Actions, Resources, Condition Keys

Actions, Resources, and Condition Keys for AWS Services - AWS Identity and Access Management  
https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_actions-resources-contextkeys.html

## CloudFormation Reference

### AWS Resource and Property Types Reference

AWS Resource and Property Types Reference - AWS CloudFormation  
https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-template-resource-type-ref.html

## SAM: Serverless Application Model

AWS サーバーレスアプリケーションモデル - アマゾン ウェブ サービス
https://aws.amazon.com/jp/serverless/sam/

awslabs/serverless-application-model: AWS Serverless Application Model (SAM) is an open-source framework for building serverless applications
https://github.com/awslabs/serverless-application-model

### AWS Serverless Application Model Template Specification

serverless-application-model/2016-10-31.md at master · awslabs/serverless-application-model
https://github.com/awslabs/serverless-application-model/blob/master/versions/2016-10-31.md

### SAM CLI Command Reference

AWS SAM CLI Command Reference - AWS Serverless Application Model
https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-cli-command-reference.html

## API Gateway

### API Gateway OpenAPI Extensions

OpenAPI に対する API Gateway 拡張 - Amazon API Gateway
https://docs.aws.amazon.com/ja_jp/apigateway/latest/developerguide/api-gateway-swagger-extensions.html

## OpenAPI, Swagger

OpenAPI Specification | Swagger
https://swagger.io/specification/

OAI/OpenAPI-Specification: The OpenAPI Specification Repository
https://github.com/OAI/OpenAPI-Specification

Home - OpenAPI Initiative
https://www.openapis.org/

OpenAPI Specification 3.0 チートシート - 朝日ネット　技術者ブログ
https://techblog.asahi-net.co.jp/entry/2019/03/04/102734

## ウェブ関連仕様 日本語訳

ウェブ関連仕様 日本語訳
https://triple-underscore.github.io/

HTTP, HTML 等の仕様を日本語訳

## OpenID Japan 資料

公開資料 | OpenID ファウンデーション・ジャパン
https://www.openid.or.jp/document/index.html

OpenID Connect 1.0, OAuth 2.0 等の日本語訳

## HTML Standard

HTML Standard
https://html.spec.whatwg.org/multipage/

HTML Standard 日本語訳
https://momdo.github.io/html/

momdo/momdo.github.io: Japanese translation of the W3C/WHATWG specification(s).
https://github.com/momdo/momdo.github.io

血統の森 web実験小屋
http://momdo.s35.xrea.com/web-html-test/index.html

## ECMAScript 2019

ECMAScript® 2019 Language Specification
https://www.ecma-international.org/ecma-262/10.0/index.html

## Markdown

Daring Fireball: Markdown Syntax Documentation
https://daringfireball.net/projects/markdown/syntax

### GFM: GitHub Flavored Markdown

Mastering Markdown · GitHub Guides
https://guides.github.com/features/mastering-markdown/

### Qiita Markdown Cheat Sheet

Markdown記法 チートシート - Qiita
https://qiita.com/Qiita/items/c686397e4a0f4f11683d

## GNU

GNUマニュアル・オンライン - GNUプロジェクト - フリーソフトウェアファウンデーション  
https://www.gnu.org/manual/manual.html

### Coreutils

GNU Coreutils: GNU Coreutils  
https://linuxjm.osdn.jp/info/GNU_coreutils/coreutils-ja.html

GNU Coreutils: Top  
https://www.gnu.org/software/coreutils/manual/html_node/index.html

## YAML: Ain't Markup Language

YAML™ Specification Index
https://yaml.org/spec/

yaml/yaml: YAML language and community information
https://github.com/yaml/yaml

YAML Ain’t Markup Language (YAML™) Version 1.2
https://yaml.org/spec/1.2/spec.html

## JSON: JavaScript Object Notation

JSON
https://www.json.org/

JSON
https://www.json.org/json-ja.html

> JSON (JavaScript Object Notation)は、軽量のデータ交換フォーマットです。人間にとって読み書きが容易で、マシンにとっても簡単にパースや生成を行なえる形式です。 JavaScriptプログラミング言語 （ECMA-262標準第3版 1999年12月）の一部をベースに作られています。 JSONは完全に言語から独立したテキスト形式ですが、C、C++、C#、Java、JavaScript、Perl、Python、その他多くのCファミリーの言語を使用するプログラマにとっては、馴染み深い規約が使われています。これらの性質が、 JSONを理想的なデータ交換言語にしています。

### JSON Schema

JSON Schema | The home of JSON Schema
https://json-schema.org/

> JSON Schema is a vocabulary that allows you to annotate and validate JSON documents.

Specification | JSON Schema
https://json-schema.org/specification.html

## .NET Core CLI

.NET Core コマンドライン インターフェイス (CLI) ツール - .NET Core CLI | Microsoft Docs  
https://docs.microsoft.com/ja-jp/dotnet/core/tools/?tabs=netcore2x

## PostgreSQL

PostgreSQL: The world's most advanced open source database  
https://www.postgresql.org/

ドキュメント | 日本PostgreSQLユーザ会  
https://www.postgresql.jp/docupage

ホーム | Let's Postgres  
https://lets.postgresql.jp/

s-hironobu/postgresqlref: PostgreSQL 全機能バイブルの原稿  
https://github.com/s-hironobu/postgresqlref

The Art of PostgreSQL: a modern PostgreSQL book in 2019  
https://theartofpostgresql.com/

## MySQL

MySQL :: MySQL Documentation  
https://dev.mysql.com/doc/

日本 MySQL ユーザ会  
http://www.mysql.gr.jp/

MySQL Casual - 資料一覧 - connpass  
https://mysql-casual.connpass.com/presentation/
