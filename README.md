何度も調べたくない事の備忘録。

# TOC

<!-- TOC -->

- [TOC](#toc)
- [`javascript`](#javascript)
    - [JSON を pretty print したい](#json-を-pretty-print-したい)
    - [AWS Lambda でエラーを発生させる](#aws-lambda-でエラーを発生させる)
    - [例外を throw する](#例外を-throw-する)
    - [sleep したい](#sleep-したい)
- [`python`](#python)
    - [python のコンストラクタで setattr を使っていい感じにインスタンス変数を設定する方法](#python-のコンストラクタで-setattr-を使っていい感じにインスタンス変数を設定する方法)
    - [`python -m json.tool`: jq が無い環境で json を見やすく表示する](#python--m-jsontool-jq-が無い環境で-json-を見やすく表示する)
    - [`python -m http.server 8000`: http server をサクッと動かす](#python--m-httpserver-8000-http-server-をサクッと動かす)
- [pip](#pip)
    - [`pip install -r requirements.txt -t ./packages`: requirements.txt からローカルにパッケージをインストールする](#pip-install--r-requirementstxt--t-packages-requirementstxt-からローカルにパッケージをインストールする)
- [java](#java)
- [`npm`: Node Package Manager](#npm-node-package-manager)
    - [`npm` cli](#npm-cli)
        - [`npm init`, `npm install package-name`: 初期セットアップ](#npm-init-npm-install-package-name-初期セットアップ)
        - [`npm install package-name@xxx`: バージョンを指定してパッケージをインストールする](#npm-install-package-namexxx-バージョンを指定してパッケージをインストールする)
    - [`npx`: execute npm package binaries](#npx-execute-npm-package-binaries)
- [Visual Studio Code](#visual-studio-code)
    - [Extensions](#extensions)
        - [PlantUML: PlantUML を書いてプレビューできる](#plantuml-plantuml-を書いてプレビューできる)
        - [Settings Sync: VS Code の設定を secret gist を使ってエクスポート、インポートできる](#settings-sync-vs-code-の設定を-secret-gist-を使ってエクスポートインポートできる)
        - [Whitespace+: スペースやタブに色付けしてくれる](#whitespace-スペースやタブに色付けしてくれる)
        - [zenkaku: 全角スペースをハイライトしてくれる](#zenkaku-全角スペースをハイライトしてくれる)
        - [Markdown TOC: 日本語使っててもいい感じに TOC を作ってくれる](#markdown-toc-日本語使っててもいい感じに-toc-を作ってくれる)
    - [ショートカット](#ショートカット)
        - [一覧](#一覧)
        - [`Command + B`: サイドバー表示をトグル](#command--b-サイドバー表示をトグル)
        - [``control + ` ``: Terminal 表示をトグル](#control----terminal-表示をトグル)
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
- [`uuidgen`: UUID を生成](#uuidgen-uuid-を生成)
- [`cut`: 受け取った文字列を分割して扱いたい](#cut-受け取った文字列を分割して扱いたい)
- [圧縮, 展開](#圧縮-展開)
    - [zip](#zip)
        - [`zip archived.zip hoge.txt`: ファイル圧縮](#zip-archivedzip-hogetxt-ファイル圧縮)
        - [`zip -r archived.zip ./hogedir`: ディレクトリ圧縮](#zip--r-archivedzip-hogedir-ディレクトリ圧縮)
        - [`zipinfo archived.zip`: 圧縮ファイルの情報を見る](#zipinfo-archivedzip-圧縮ファイルの情報を見る)
    - [`unzip archived.zip`: 圧縮ファイルの展開](#unzip-archivedzip-圧縮ファイルの展開)
    - [`gunzip`](#gunzip)
        - [`gunzip -r mydirectory`: ディレクトリを指定して再帰的に圧縮ファイルを展開](#gunzip--r-mydirectory-ディレクトリを指定して再帰的に圧縮ファイルを展開)
- [パフォーマンス系](#パフォーマンス系)
    - [CPU 使用率を上げたい](#cpu-使用率を上げたい)
    - [`seq 10 | xargs -t -P10 -n1 sh -c 'echo hoge'`: 並列にコマンドを実行したい](#seq-10--xargs--t--p10--n1-sh--c-echo-hoge-並列にコマンドを実行したい)
    - [`time`: コマンドにかかる時間を計測したい](#time-コマンドにかかる時間を計測したい)
- [`dd`: dataset definition](#dd-dataset-definition)
    - [ダミーファイルを作りたい](#ダミーファイルを作りたい)
- [jq](#jq)
    - [`jq -r '.hoge'`: 抽出した文字列からダブルクオートを取り除く](#jq--r-hoge-抽出した文字列からダブルクオートを取り除く)
    - [`jq fromjson`: エスケープされた json を整形する](#jq-fromjson-エスケープされた-json-を整形する)
    - [`jq length`: json 要素の数をカウントする](#jq-length-json-要素の数をカウントする)
- [Git](#git)
    - [`git clean -i -d`: git 管理してないファイルやディレクトリを削除](#git-clean--i--d-git-管理してないファイルやディレクトリを削除)
    - [`git checkout .`: ファイルの変更を commit せず取り消す](#git-checkout--ファイルの変更を-commit-せず取り消す)
    - [`.gitignore` あれこれ](#gitignore-あれこれ)
    - [`git rm filename`: Git で管理しているファイルを削除したい](#git-rm-filename-git-で管理しているファイルを削除したい)
    - [`git rm --cached filename`: 特定ファイルを削除せずに Git 管理から外したい](#git-rm---cached-filename-特定ファイルを削除せずに-git-管理から外したい)
    - [`git log -1`, `git log -n 1`: 直前の commit log を見たい](#git-log--1-git-log--n-1-直前の-commit-log-を見たい)
    - [`git diff --cached filename`: add したファイルの diff が見たい](#git-diff---cached-filename-add-したファイルの-diff-が見たい)
    - [ローカルでトピックブランチ作ってマージして消す](#ローカルでトピックブランチ作ってマージして消す)
    - [`git commit --amend -m 'fix message'`: 直前の commit メッセージ変更](#git-commit---amend--m-fix-message-直前の-commit-メッセージ変更)
    - [直前の commit 取り消し](#直前の-commit-取り消し)
    - [`git reset .`: `git add` の取り消し](#git-reset--git-add-の取り消し)
    - [ファイルやディレクトリのリネーム](#ファイルやディレクトリのリネーム)
    - [プライベートな GitHub アカウントで使ってる Git ユーザーを設定する](#プライベートな-github-アカウントで使ってる-git-ユーザーを設定する)
- [AWS CLI](#aws-cli)
    - [`aws configure --profile hoge`: profile 追加](#aws-configure---profile-hoge-profile-追加)
    - [AWS CLI で IAM Role のクレデンシャルを使う](#aws-cli-で-iam-role-のクレデンシャルを使う)
    - [parameter を json で良い感じに入力する方法](#parameter-を-json-で良い感じに入力する方法)
        - [`--generate-cli-skeleton` で json のフォーマットを確認](#--generate-cli-skeleton-で-json-のフォーマットを確認)
        - [ヒアドキュメントで json を生成](#ヒアドキュメントで-json-を生成)
        - [コマンドを実行](#コマンドを実行)
    - [Lambda](#lambda)
        - [`invoke`: Lambda 関数の起動](#invoke-lambda-関数の起動)
    - [Comprehend](#comprehend)
        - [`detect-dominant-language`: 言語検出](#detect-dominant-language-言語検出)
        - [`detect-entities`: エンティティ検出](#detect-entities-エンティティ検出)
        - [`detect-sentiment`: 感情分析](#detect-sentiment-感情分析)
        - [`detect-key-phrases`: キーフレーズ検出](#detect-key-phrases-キーフレーズ検出)
    - [Pinpoint](#pinpoint)
        - [`put-events`: イベント送信](#put-events-イベント送信)
        - [`phone-number-validate`: 電話番号の検証](#phone-number-validate-電話番号の検証)
        - [`update-endpoint`: エンドポイントの登録、更新](#update-endpoint-エンドポイントの登録更新)
        - [`get-entpoid`: エンドポイント取得](#get-entpoid-エンドポイント取得)
    - [ECS/Fargate](#ecsfargate)
        - [`run-task`: タスク実行](#run-task-タスク実行)
            - [Fargage](#fargage)
            - [EC2](#ec2)
    - [Secrets Manager](#secrets-manager)
        - [`get-random-password`: ランダムパスワード生成](#get-random-password-ランダムパスワード生成)
    - [SQS](#sqs)
        - [`send-message`: キューにメッセージ送信](#send-message-キューにメッセージ送信)
        - [`receive-message`: キューからメッセージ受信](#receive-message-キューからメッセージ受信)
        - [`delete-message`: メッセージ削除](#delete-message-メッセージ削除)
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
    - [Cognito User Pool](#cognito-user-pool)
        - [ADMIN NO SRP AUTH による認証](#admin-no-srp-auth-による認証)
        - [USER PASSWORD AUTH による認証](#user-password-auth-による認証)
    - [Cognito ID Pool](#cognito-id-pool)
        - [Enhanced Flow](#enhanced-flow)
            - [UnAuth](#unauth)
            - [Auth](#auth)
- [AWS SAM CLI](#aws-sam-cli)
- [AWS Chalice](#aws-chalice)
- [ランダム文字列生成](#ランダム文字列生成)
- [pandoc を使って markdown を XWiki 記法に変換](#pandoc-を使って-markdown-を-xwiki-記法に変換)
    - [参考](#参考)
- [`curl`](#curl)
    - [ファイルをアップロードしたい](#ファイルをアップロードしたい)
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
    - [X.509 仕様](#x509-仕様)
    - [`openssl dgst -sha256`: SHA 256 でメッセージダイジェスト出力](#openssl-dgst--sha256-sha-256-でメッセージダイジェスト出力)
    - [サーバーに設定されている証明書の確認](#サーバーに設定されている証明書の確認)
    - [HTTP リクエスト](#http-リクエスト)
- [`date`](#date)
    - [unixtime を JST に変換](#unixtime-を-jst-に変換)
    - [unixtime を UTC に変換](#unixtime-を-utc-に変換)
    - [現在時刻を unixtime で出力](#現在時刻を-unixtime-で出力)
    - [現在時刻を ISO 8601 で出力](#現在時刻を-iso-8601-で出力)
        - [JST](#jst)
        - [UTC](#utc)
    - [参考](#参考)
- [`ls`](#ls)
    - [`ls -1`: ファイル名のみ1列でリスト](#ls--1-ファイル名のみ1列でリスト)
- [`tree`](#tree)
    - [`tree -I nodemodule`: 特定ディレクトリを省いて tree 表示したい](#tree--i-nodemodule-特定ディレクトリを省いて-tree-表示したい)
- [XML を jq 的に整形したい](#xml-を-jq-的に整形したい)
    - [参考](#参考)
- [hugo](#hugo)
    - [`hugo`: static page のビルド](#hugo-static-page-のビルド)
- [環境変数一覧を表示したい](#環境変数一覧を表示したい)
- [bash](#bash)
    - [`while`](#while)
    - [`for`](#for)
    - [交互にコマンドを実行するスクリプト](#交互にコマンドを実行するスクリプト)
- [英語](#英語)
    - [footnote: 脚注、補足説明、注釈、下記](#footnote-脚注補足説明注釈下記)
    - [Even if: たとえ](#even-if-たとえ)
    - [evicted: 立ち退かせる、追い立てる](#evicted-立ち退かせる追い立てる)
    - [dip: 浸す、すくい上げる、少し下げる](#dip-浸すすくい上げる少し下げる)
    - [referred: 言及する、触れる、引き合いに出す](#referred-言及する触れる引き合いに出す)
    - [callout: ... を大声で呼ぶ、 ... を呼び出す、出勤させる、喧嘩を挑む、発呼](#callout--を大声で呼ぶ--を呼び出す出勤させる喧嘩を挑む発呼)
    - [夏時間: Daylight Savings Time, Suumer Time](#夏時間-daylight-savings-time-suumer-time)
    - [glance: 一見、チラ見、きらめき](#glance-一見チラ見きらめき)
    - [significant: 重要な、意味深な、かなりの](#significant-重要な意味深なかなりの)
    - [steep: 急な、激しい、大げさな、険しい、法外な、途方もなく高い](#steep-急な激しい大げさな険しい法外な途方もなく高い)
    - [Dedicated: 専用の、特定の目的のための、献身的な](#dedicated-専用の特定の目的のための献身的な)
    - [Differentiate: 区別する、識別する、差異を生じさせる](#differentiate-区別する識別する差異を生じさせる)
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
    - [CORS な API をテストできるサイト](#cors-な-api-をテストできるサイト)
    - [markdown の table ジェネレーター](#markdown-の-table-ジェネレーター)
    - [JSON を diff できるサイト](#json-を-diff-できるサイト)
    - [JSON を良い感じに見れる Viewer](#json-を良い感じに見れる-viewer)
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
- [便利なツール](#便利なツール)
    - [iOS, Android といったモバイルデバイスの通信状況を確認したい](#ios-android-といったモバイルデバイスの通信状況を確認したい)
- [仕様とかリファレンスとか](#仕様とかリファレンスとか)
    - [AWS Guides and API Reference](#aws-guides-and-api-reference)
    - [AWS CLI Reference](#aws-cli-reference)
    - [AWS IAM](#aws-iam)
        - [IAM ID](#iam-id)
        - [Actions, Resources, Condition Keys](#actions-resources-condition-keys)
    - [AWS Encryption SDK](#aws-encryption-sdk)
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
    - [CPython](#cpython)
    - [Java](#java)
    - [WebSocket](#websocket)

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

## AWS Lambda でエラーを発生させる

```js
exports.handler = (event, context, callback) => {
    callback("error");
};
```

Node.js の AWS Lambda 関数ハンドラー - AWS Lambda
https://docs.aws.amazon.com/ja_jp/lambda/latest/dg/nodejs-prog-model-handler.html

> 3 番目の引数 callback は、レスポンスを送信するために non-async 関数で呼び出すことができる関数です。コールバック関数は、Error とレスポンスの 2 つの引数を取ります。応答オブジェクトは、JSON.stringify と互換性がある必要があります。 

Node.js での AWS Lambda Context オブジェクト - AWS Lambda
https://docs.aws.amazon.com/ja_jp/lambda/latest/dg/nodejs-prog-model-context.html

> callbackWaitsForEmptyEventLoop – false に設定して、Node.js イベントループが空になるまで待機せずに、コールバックが実行されるとすぐにレスポンスを送信します。これが false の場合、未完了のイベントは、次の呼び出し中に実行され続けます。


## 例外を throw する

```js
exports.handler = (event, context, callback) => {
    throw true;
};
```

throw - JavaScript | MDN
https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Statements/throw

## sleep したい

setTimeout 使うなら

```js
exports.handler = (event, context, callback) => {
    setTimeout(function(){
    }, 11000);
};
```

async, await 使うなら

```js
function sleep(waitSec) {
    return new Promise(function (resolve) {
        setTimeout(function() { resolve() }, waitSec);
    });
};

exports.handler = async (event, context, callback) => {
    console.log(event);
    await sleep(5000);
    callback(null, "Hello, " + event.who + "!");
};
```

# `python`

3.6.9 Documentation  
https://docs.python.org/ja/3.6/

## python のコンストラクタで setattr を使っていい感じにインスタンス変数を設定する方法

こんな感じで取得できる API があったとして

```bash
% aws ec2 describe-regions --region-names ap-northeast-1
{
    "Regions": [
        {
            "Endpoint": "ec2.ap-northeast-1.amazonaws.com",
            "RegionName": "ap-northeast-1",
            "OptInStatus": "opt-in-not-required"
        }
    ]
}
```

Region クラスを扱いたい場合・・・

```py
import boto3

class Region:
    def __init__(self,region):
        region_info = region

        # インスタンス生成時に dict を渡して key, value を setattr でインスタンス変数に設定する
        for key, value in region_info.items():
            setattr(self, str(key), value)

client = boto3.client('ec2')
response = client.describe_regions(RegionNames=['ap-northeast-1'])

tokyo = Region(response['Regions'][0])
print(vars(tokyo))
```

実行するとこんな感じ

```bash
% python script.py
{'Endpoint': 'ec2.ap-northeast-1.amazonaws.com', 'RegionName': 'ap-northeast-1', 'OptInStatus': 'opt-in-not-required'}
```

API で取得した key, value をインスタンス変数として設定できた

組み込み関数 — Python 3.8.2rc1 ドキュメント  
https://docs.python.org/ja/3/library/functions.html#setattr

> setattr(object, name, value)  
> getattr() の相方です。引数はオブジェクト、文字列、それから任意の値です。文字列は既存の属性または新たな属性の名前にできます。この関数は指定したオブジェクトが許せば、値を属性に関連付けます。例えば、 setattr(x, 'foobar', 123) は x.foobar = 123 と等価です。

組み込み関数 — Python 3.8.2rc1 ドキュメント  
https://docs.python.org/ja/3/library/functions.html#vars

> vars([object])  
> モジュール、クラス、インスタンス、あるいはそれ以外の __dict__ 属性を持つオブジェクトの、 __dict__ 属性を返します。  
> モジュールやインスタンスのようなオブジェクトは、更新可能な __dict__ 属性を持っています。ただし、それ以外のオブジェクトでは __dict__ 属性への書き込みが制限されている場合があります。書き込みに制限がある例としては、辞書を直接更新されることを防ぐために types.MappingProxyType を使っているクラスがあります。  
> 引数がなければ、vars() は locals() のように振る舞います。ただし、辞書 locals への更新は無視されるため、辞書 locals は読み出し時のみ有用であることに注意してください。

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

# pip

pip - The Python Package Installer — pip 20.0.2 documentation
https://pip.pypa.io/en/stable/  

pip — pip 20.0.2 documentation  
https://pip.pypa.io/en/stable/reference/pip/

pypa/pip: The Python package installer  
https://github.com/pypa/pip

PyPI · The Python Package Index  
https://pypi.org/

## `pip install -r requirements.txt -t ./packages`: requirements.txt からローカルにパッケージをインストールする

```bash
% cat requirements.txt 
boto3
% pip install -r requirements.txt -t ./packages
```

# java

Java Documentation - Get Started  
https://docs.oracle.com/en/java/index.html

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

### PlantUML: PlantUML を書いてプレビューできる

PlantUML - Visual Studio Marketplace  
https://marketplace.visualstudio.com/items?itemName=jebbs.plantuml

別途 PlantUML サーバーが必要になるが、公式の Docker Image があるので、これを使うと楽

plantuml/plantuml-server: PlantUML Online Server  
https://github.com/plantuml/plantuml-server

```bash
docker run -p 8080:8080 plantuml/plantuml-server:jetty
```

PlantUML の書き方

PlantUML Cheat Sheet - Qiita  
https://qiita.com/ogomr/items/0b5c4de7f38fd1482a48

https://plantuml.com/ が公式サイトだが、証明書が切れてる？

### Settings Sync: VS Code の設定を secret gist を使ってエクスポート、インポートできる

Settings Sync - Visual Studio Marketplace  
https://marketplace.visualstudio.com/items?itemName=Shan.code-settings-sync

PC を移行する時に便利

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

### `Command + B`: サイドバー表示をトグル

### ``control + ` ``: Terminal 表示をトグル

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
MYSQL_PASSWORD=my-secret-pw
CONTAINER_NAME=my-mysql-container
# MySQL が Ready するまで多少時間がかかるため sleep している
docker run --name $CONTAINER_NAME -e MYSQL_ROOT_PASSWORD=$MYSQL_PASSWORD -d mysql:latest; sleep 30s; docker exec -it $CONTAINER_NAME mysql -u root -p$MYSQL_PASSWORD
docker stop $CONTAINER_NAME; docker rm $CONTAINER_NAME
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

# `uuidgen`: UUID を生成

uuidgen  
https://www.freebsd.org/cgi/man.cgi?query=uuidgen

Man page of UUIDGEN  
https://linuxjm.osdn.jp/html/e2fsprogs/man1/uuidgen.1.html

```bash
$ uuidgen
E71163D4-6570-4A9A-984D-9EC5B708F682

# 小文字で出力
$ tr '[A-Z]' '[a-z]' <<<$(uuidgen)
a272224a-5e5f-43bc-978c-4bdfc0ded246

# 大文字で出力
$ tr '[a-z]' '[A-Z' <<<$(uuidgen)
A272224A-5E5F-43BC-978C-4BDFC0DED246
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

## `gunzip`

gunzip(1): compress/expand files - Linux man page  
https://linux.die.net/man/1/gunzip

gunzip  
https://www.freebsd.org/cgi/man.cgi?query=gunzip

### `gunzip -r mydirectory`: ディレクトリを指定して再帰的に圧縮ファイルを展開

```bash
unzip -r ./mydirectory
```

gunzip(1): compress/expand files - Linux man page  
https://linux.die.net/man/1/gunzip

> -r, --recursive  
> This option is used to gzip the files in	a directory tree individually, using	the fts(3) library.

gunzip  
https://www.freebsd.org/cgi/man.cgi?query=gunzip

> -r --recursive  
> Travel the directory structure recursively. If any of the file names specified on the command line are directories, gzip will descend into the directory and compress all the files it finds there (or decompress them in the case of gunzip ). 

# パフォーマンス系

## CPU 使用率を上げたい

```bash
yes > /dev/null &
```

## `seq 10 | xargs -t -P10 -n1 sh -c 'echo hoge'`: 並列にコマンドを実行したい

```bash
seq 10 | xargs -t -P10 -n1 sh -c 'echo hoge'
```

`seq x` と `-Px` で並列して実行されるプロセス数を指定。これは `-n1` で seq で出力される数値を1つずつ xargs で指定しているコマンドの引数にする。
上記例であれば `sh -c 'echo hoge' 1` のようになる。で、実質 1 は無視されるので `echo hoge` が実行される。

`-t` で実行されるコマンドを表示してくれる。

xargsでコマンドを並列実行 - Qiita  
https://qiita.com/aosho235/items/231d6d12f56debc515f9

Man page of XARGS  
https://linuxjm.osdn.jp/html/GNU_findutils/man1/xargs.1.html

GNU Parallel - GNU Project - Free Software Foundation  
https://www.gnu.org/software/parallel/

## `time`: コマンドにかかる時間を計測したい

Man page of TIME  
https://linuxjm.osdn.jp/html/LDP_man-pages/man1/time.1.html

time  
https://www.freebsd.org/cgi/man.cgi?query=time

```bash
$ time echo hoge
hoge

real    0m0.001s
user    0m0.000s
sys     0m0.000s

$ time sleep 1s; echo hoge

real    0m1.156s
user    0m0.001s
sys     0m0.014s
hoge
```

# `dd`: dataset definition

IBM メインフレームの言語ステートメントが由来らしい。

dd (UNIX) - Wikipedia  
https://ja.wikipedia.org/wiki/Dd_(UNIX)

> dataset definitionの略であるが、IBMのメインフレームのJob Control Language（ジョブ制御言語、JCL）の「DD文」（DD statement）に由来する

dd  
https://www.freebsd.org/cgi/man.cgi?query=dd

Man page of DD  
https://linuxjm.osdn.jp/html/GNU_coreutils/man1/dd.1.html

## ダミーファイルを作りたい

Mac, BSD

```bash
# 1GB のファイル作成
$ dd if=/dev/zero of=1G.txt bs=1024000 count=1000
```

Linux

```bash
# 1GB のファイル作成
$ dd if=/dev/zero of=1G.txt bs=1M count=1000
```

# jq

jq  
https://stedolan.github.io/jq/

stedolan/jq: Command-line JSON processor  
https://github.com/stedolan/jq

## `jq -r '.hoge'`: 抽出した文字列からダブルクオートを取り除く

jq Manual (development version)
https://stedolan.github.io/jq/manual/#Invokingjq

> --raw-output / -r:
> 
> With this option, if the filter’s result is a string then it will be written directly to standard output rather than being formatted as a JSON string with quotes. This can be useful for making jq filters talk to non-JSON-based systems.

サンプル

```bash
JSON='{"Users":[{"name": "hoge"},{"name": "fuga"},{"name": "bar"}]}'
echo $JSON | jq
echo $JSON | jq '.Users[0].name'
echo $JSON | jq -r '.Users[0].name'
```

実行例

```bash
$ JSON='{"Users":[{"name": "hoge"},{"name": "fuga"},{"name": "bar"}]}'
$ echo $JSON | jq
{
  "Users": [
    {
      "name": "hoge"
    },
    {
      "name": "fuga"
    },
    {
      "name": "bar"
    }
  ]
}
$ echo $JSON | jq '.Users[0].name'
"hoge"
$ echo $JSON | jq -r '.Users[0].name'
hoge
```

## `jq fromjson`: エスケープされた json を整形する

jq Manual (development version)
https://stedolan.github.io/jq/manual/#Builtinoperatorsandfunctions

> Convert to/from JSON
> 
> The `tojson` and `fromjson` builtins dump values as JSON texts or parse JSON texts into values, respectively.  
> The tojson builtin differs from tostring in that tostring returns strings unmodified, while tojson encodes strings as JSON strings.

サンプル

```bash
$ cat << EOS | pbcopy
{
  "a" : 1,
  "b" : 2,
  "c" : "{\"id\":\"hoge\",\"parent\":\"abc\"}\n"
}
EOS

$ pbpaste | jq .
{
  "a": 1,
  "b": 2,
  "c": "{\"id\":\"hoge\",\"parent\":\"abc\"}\n"
}
$ pbpaste | jq '.c'
"{\"id\":\"hoge\",\"parent\":\"abc\"}\n"
$ pbpaste | jq '.c | fromjson'
{
  "id": "hoge",
  "parent": "abc"
}
```

## `jq length`: json 要素の数をカウントする

jq Manual (development version)  
https://stedolan.github.io/jq/manual/#Builtinoperatorsandfunctions

> length
> 
> The builtin function length gets the length of various different types of value:
> - The length of a string is the number of Unicode codepoints it contains (which will be the same as its JSON-encoded length in bytes if it’s pure ASCII).
> - The length of an array is the number of elements.
> - The length of an object is the number of key-value pairs.
> - The length of null is zero.

サンプル

```bash
JSON='{"Users":[{"name": "hoge"},{"name": "fuga"},{"name": "bar"}]}'
echo $JSON | jq
echo $JSON | jq length  
echo $JSON | jq '.Users | length'
```

実行例

```bash
$ JSON='{"Users":[{"name": "hoge"},{"name": "fuga"},{"name": "bar"}]}'
$ echo $JSON | jq
{
  "Users": [
    {
      "name": "hoge"
    },
    {
      "name": "fuga"
    },
    {
      "name": "bar"
    }
  ]
}
$ echo $JSON | jq length  
1
$ echo $JSON | jq '.Users | length'
3
```

# Git

Git - Reference  
https://git-scm.com/docs

## `git clean -i -d`: git 管理してないファイルやディレクトリを削除

Git - git-clean Documentation  
https://git-scm.com/docs/git-clean

```bash
$ git clean -i -d
```

`-d` は directory も削除対象に含めるオプション

> -d  
> Normally, when no <path> is specified, git clean will not recurse into untracked directories to avoid removing too much. Specify -d to have it recurse into such directories as well. If any paths are specified, -d is irrelevant; all untracked files matching the specified paths (with exceptions for nested git directories mentioned under --force) will be removed.

`-i` は削除する際にインタラクティブモードによって確認を行うオプション

> -i  
> --interactive  
> Show what would be done and clean files interactively. See “Interactive mode” for details.


## `git checkout .`: ファイルの変更を commit せず取り消す

Git - git-checkout Documentation
https://git-scm.com/docs/git-checkout

```bash
$ git checkout .
```

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

## `git reset .`: `git add` の取り消し

```bash
git reset .
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

## parameter を json で良い感じに入力する方法

describe-regions — AWS CLI 1.16.266 Command Reference
https://docs.aws.amazon.com/cli/latest/reference/ec2/describe-regions.html

describe-regions を例に。

### `--generate-cli-skeleton` で json のフォーマットを確認

必須ではないパラメーターはよしなに削る

```bash
$ aws ec2 describe-regions --generate-cli-skeleton
{
    "Filters": [
        {
            "Name": "",
            "Values": [
                ""
            ]
        }
    ],
    "RegionNames": [
        ""
    ],
    "DryRun": true,
    "AllRegions": true
}
```

### ヒアドキュメントで json を生成

シェル変数をよしなに使う

```bash
JSON_FILENAME=parameter.json
FILTER_ENDPOINT=endpoint
FILTER_ENDPOINT_VALUES='*us*'
cat << EOS > $JSON_FILENAME
{
    "Filters": [
        {
            "Name": "${FILTER_ENDPOINT}",
            "Values": [
                "${FILTER_ENDPOINT_VALUES}"
            ]
        }
    ]
}
EOS

```

### コマンドを実行

```bash
$ aws ec2 describe-regions --cli-input-json file://./$JSON_FILENAME
$ rm $JSON_FILENAME
```

## Lambda

### `invoke`: Lambda 関数の起動

invoke — AWS CLI 1.16.283 Command Reference  
https://docs.aws.amazon.com/cli/latest/reference/lambda/invoke.html

```bash
FUNCTION_NAME=myfunction

# base64 command
aws lambda invoke --function-name $FUNCTION_NAME --payload '{ "name": "Bob" }' --log-type Tail outfile --query 'LogResult' --output text | base64 -D

# openssl command
aws lambda invoke --function-name $FUNCTION_NAME --payload '{ "name": "Bob" }' --log-type Tail outfile --query 'LogResult' --output text | openssl base64 -d

# remove event outfile
rm outfile
```

## Comprehend

### `detect-dominant-language`: 言語検出

detect-dominant-language — AWS CLI 1.16.281 Command Reference  
https://docs.aws.amazon.com/cli/latest/reference/comprehend/detect-dominant-language.html

```bash
aws --region us-east-1 comprehend detect-dominant-language --text "こんにちは"
```

### `detect-entities`: エンティティ検出

detect-entities — AWS CLI 1.16.281 Command Reference  
https://docs.aws.amazon.com/cli/latest/reference/comprehend/detect-entities.html

```bash
aws --region us-east-1 comprehend detect-entities --language-code ja --text "Amazon Comprehend は機械学習を使用して、構造化されていないデータのインサイトと関係を明らかにします。このサービスは、テキストの言語を識別し、キーフレーズ、場所、人物、ブランド、またはイベントを抽出し、テキストがどの程度肯定的か否定的かを理解し、トークン分割や品詞を使用してテキストを分析し、テキストファイルのコレクションをトピックごとに自動的に整理します。Amazon Comprehend の AutoML 機能を使用して、組織のニーズに合わせて独自にカスタマイズされたエンティティまたはテキスト分類モデルのカスタムセットを構築することもできます。"
```

### `detect-sentiment`: 感情分析

detect-sentiment — AWS CLI 1.16.281 Command Reference  
https://docs.aws.amazon.com/cli/latest/reference/comprehend/detect-sentiment.html

```bash
aws --region us-east-1 comprehend detect-sentiment --language-code ja --text "こんにちは"
```

### `detect-key-phrases`: キーフレーズ検出

```bash
aws --region us-east-1 comprehend detect-key-phrases --language-code ja --text "Amazon Comprehend は機械学習を使用して、構造化されていないデータのインサイトと関係を明らかにします。このサービスは、テキストの言語を識別し、キーフレーズ、場所、人物、ブランド、またはイベントを抽出し、テキストがどの程度肯定的か否定的かを理解し、トークン分割や品詞を使用してテキストを分析し、テキストファイルのコレクションをトピックごとに自動的に整理します。Amazon Comprehend の AutoML 機能を使用して、組織のニーズに合わせて独自にカスタマイズされたエンティティまたはテキスト分類モデルのカスタムセットを構築することもできます。"
```

## Pinpoint

pinpoint — AWS CLI 1.16.246 Command Reference  
https://docs.aws.amazon.com/cli/latest/reference/pinpoint/index.html

### `put-events`: イベント送信

put-events — AWS CLI 1.16.266 Command Reference  
https://docs.aws.amazon.com/cli/latest/reference/pinpoint/put-events.html

```bash
REGION=us-east-1
APPLICATION_ID=xxx
ADDRESS=sampleuser@example.com
USER_ID=sampleuser
TIMESTAMP=$(date -u +%FT%TZ)
JSON_FILENAME=$(uuidgen).json
cat << EOS > $JSON_FILENAME
{
    "ApplicationId": "${APPLICATION_ID}",
    "EventsRequest": {
        "BatchItem": {
            "MyItem": {
                "Endpoint": {
                    "Address": "${ADDRESS}",
                    "ChannelType": "EMAIL",
                    "User": {
                        "UserId": "${USER_ID}"
                    }
                },
                "Events": {
                    "MyEvents": {
                        "EventType": "MyEventType",
                        "Timestamp": "${TIMESTAMP}"
                    }
                }
            }
        }
    }
}
EOS
aws --region $REGION pinpoint put-events --cli-input-json file://./$JSON_FILENAME
```

### `phone-number-validate`: 電話番号の検証

Amazon Pinpoint での電話番号の検証 - Amazon Pinpoint  
https://docs.aws.amazon.com/ja_jp/pinpoint/latest/developerguide/validate-phone-numbers.html

```bash
REGION=us-east-1
PHONE_NUMBER=+81xxx
aws --region $REGION pinpoint phone-number-validate --number-validate-request PhoneNumber=$PHONE_NUMBER
```

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

## Secrets Manager

### `get-random-password`: ランダムパスワード生成

get-random-password — AWS CLI 1.16.268 Command Reference  
https://docs.aws.amazon.com/cli/latest/reference/secretsmanager/get-random-password.html

```bash
aws secretsmanager get-random-password

# test 抽出
aws secretsmanager get-random-password --output text
PASSWORD=$(aws secretsmanager get-random-password --output text)

# パスワードの長さ指定したりできる
aws secretsmanager get-random-password --password-length 6
```

## SQS

### `send-message`: キューにメッセージ送信

```bash
QUEUE_URL=xxx
aws sqs send-message --queue-url $QUEUE_URL --message-body hoge

# FIFO Queue
MESSAGE_GROUP_ID=mygroupid
aws sqs send-message --queue-url $QUEUE_URL --message-group-id $MESSAGE_GROUP_ID --message-body hoge
```

send-message — AWS CLI 1.16.277 Command Reference  
https://docs.aws.amazon.com/cli/latest/reference/sqs/send-message.html


### `receive-message`: キューからメッセージ受信

```bash
QUEUE_URL=xxx
aws sqs receive-message --queue-url $QUEUE_URL --attribute-names All
```

receive-message — AWS CLI 1.16.277 Command Reference  
https://docs.aws.amazon.com/cli/latest/reference/sqs/receive-message.html

### `delete-message`: メッセージ削除

```bash
QUEUE_URL=xxx
aws sqs receive-message --queue-url $QUEUE_URL

RECEIPT_HANDLE=yyy
aws sqs delete-message --queue-url $QUEUE_URL --receipt-handle $RECEIPT_HANDLE
```

delete-message — AWS CLI 1.16.277 Command Reference  
https://docs.aws.amazon.com/cli/latest/reference/sqs/delete-message.html

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

# template で IAM リソース場合
aws cloudformation deploy --template-file ./mytemplate.yaml --stack-name mystack --capabilities CAPABILITY_IAM

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

## Cognito User Pool

### ADMIN NO SRP AUTH による認証

admin-initiate-auth — AWS CLI 1.16.266 Command Reference  
https://docs.aws.amazon.com/cli/latest/reference/cognito-idp/admin-initiate-auth.html

```bash
USER_POOL_ID=xxx
CLIENT_ID=xxx
USERNAME=sampleuser
PASSWORD=mypassword
AUTH_FLOW=ADMIN_NO_SRP_AUTH
aws cognito-idp admin-initiate-auth --user-pool-id $USER_POOL_ID --client-id $CLIENT_ID --auth-flow $AUTH_FLOW --auth-parameters USERNAME=$USERNAME,PASSWORD=$PASSWORD
```

### USER PASSWORD AUTH による認証

initiate-auth — AWS CLI 1.16.266 Command Reference  
https://docs.aws.amazon.com/cli/latest/reference/cognito-idp/initiate-auth.html

```bash
AUTH_FLOW=USER_PASSWORD_AUTH
USERNAME=sampleuser
PASSWORD=mypassword
CLIENT_ID=xxx
aws cognito-idp initiate-auth --auth-flow $AUTH_FLOW --auth-parameters USERNAME=$USERNAME,PASSWORD=$PASSWORD --client-id $CLIENT_ID
```

## Cognito ID Pool

### Enhanced Flow

#### UnAuth

```bash
ID_POOL_ID=xxx
IDENTITY_ID=$(aws cognito-identity get-id --identity-pool-id $ID_POOL_ID --output text)
aws cognito-identity get-credentials-for-identity --identity-id $IDENTITY_ID

export AWS_ACCESS_KEY_ID=xxx
export AWS_SECRET_ACCESS_KEY=xxx
export AWS_SESSION_TOKEN=xxx

aws sts get-caller-identity

unset AWS_ACCESS_KEY_ID
unset AWS_SECRET_ACCESS_KEY
unset AWS_SESSION_TOKEN
```

#### Auth

```bash
REGION=ap-northeast-1
USER_POOL_ID=ap-northeast-1_xxx
CLIENT_ID=xxx
USERNAME=sampleuser
PASSWORD=mypassword
AUTH_FLOW=ADMIN_NO_SRP_AUTH
ID_TOKEN=$(aws cognito-idp admin-initiate-auth --user-pool-id $USER_POOL_ID --client-id $CLIENT_ID --auth-flow $AUTH_FLOW --auth-parameters USERNAME=$USERNAME,PASSWORD=$PASSWORD --query AuthenticationResult.IdToken --output text)

ID_POOL_ID=xxx
IDENTITY_ID=$(aws cognito-identity get-id --identity-pool-id $ID_POOL_ID --logins cognito-idp.$REGION.amazonaws.com/$USER_POOL_ID=$ID_TOKEN --output text)

aws cognito-identity get-credentials-for-identity --identity-id $IDENTITY_ID --logins cognito-idp.$REGION.amazonaws.com/$USER_POOL_ID=$ID_TOKEN

export AWS_ACCESS_KEY_ID=xxx
export AWS_SECRET_ACCESS_KEY=xxx
export AWS_SESSION_TOKEN=xxx

aws sts get-caller-identity

unset AWS_ACCESS_KEY_ID
unset AWS_SECRET_ACCESS_KEY
unset AWS_SESSION_TOKEN
```

# AWS SAM CLI

AWS SAM CLI Command Reference - AWS Serverless Application Model  
https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-cli-command-reference.html

```bash
STACK_NAME=mystack
S3_BUCKET=mybucket
sam build
sam package --output-template packaged.yaml --s3-bucket $S3_BUCKET
sam deploy --template-file ./packaged.yaml --stack-name $STACK_NAME --capabilities CAPABILITY_IAM
aws cloudformation delete-stack --stack-name $STACK_NAME
```

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
# output to file
pandoc -f markdown -t xwiki -o converted.wiki original.md 

# output clipboard (Mac)
pandoc -f markdown original.md -t xwiki | pbcopy
```

`-f`: from
`-t`: to
`-o`: output

## 参考

Pandoc - Pandoc User’s Guide
https://pandoc.org/MANUAL.html

# `curl`

## ファイルをアップロードしたい

```bash
FILENAME=DUMMY_IMAGE.png
curl https://via.placeholder.com/150 -o $FILENAME
ENDPOINT=https://example.com
curl -X POST $ENDPOINT -F hoge=fuga -F foo=bar -F "file=@$FILENAME;type=image/png"
```

curl - How To Use  
https://curl.haxx.se/docs/manpage.html#-o

curl - How To Use  
https://curl.haxx.se/docs/manpage.html#-F

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

/docs/man1.1.1/man1/index.html  
https://www.openssl.org/docs/man1.1.1/man1/

## X.509 仕様

RFC 5280 - Internet X.509 Public Key Infrastructure Certificate and Certificate Revocation List (CRL) Profile  
https://tools.ietf.org/html/rfc5280

Internet X.509 PKI Certificate and Certificate Revocation List (CRL) Profile  
https://www.ipa.go.jp/security/rfc/RFC5280-00JA.html


## `openssl dgst -sha256`: SHA 256 でメッセージダイジェスト出力

/docs/man1.0.2/man1/openssl-dgst.html  
https://www.openssl.org/docs/man1.0.2/man1/openssl-dgst.html

```bash
echo "hoge" | openssl dgst -sha256
```

実行例

```bash
$ echo "hoge" | openssl dgst -sha256
(stdin)= 2e0390eb024a52963db7b95e84a9c2b12c004054a7bad9a97ec0c7c89d4681d2
```

## サーバーに設定されている証明書の確認

```bash
DOMAIN=www.example.com

echo "Q" | openssl s_client -connect $DOMAIN:443 -showcerts

# SNI
echo "Q" | openssl s_client -connect $DOMAIN:443 -servername hoge.example.com -showcerts

# 証明書の有効期限を確認する
# notBefore が有効期限の始まり。
# notAfter が有効期限の終わり。
echo "Q" | openssl s_client -connect $DOMAIN:443 | openssl x509 -noout -dates

# シリアルナンバー確認
echo "Q" | openssl s_client -connect $DOMAIN:443 | openssl x509 -noout -serial

# SAN (Subject Alternative Names) 確認
echo "Q" | openssl s_client -connect $DOMAIN:443 | openssl x509 -text | grep DNS
```

## HTTP リクエスト

```bash
$ openssl s_client -connect example.com:443
# 証明書情報
GET / HTTP/1.1
Host:example.com
# ENTER
```

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

# `ls`

Man page of LS  
https://linuxjm.osdn.jp/html/gnumaniak/man1/ls.1.html

ls  
https://www.freebsd.org/cgi/man.cgi?ls

## `ls -1`: ファイル名のみ1列でリスト

```bash
ls -1
```

# `tree`

tree(1) - Linux man page  
https://linux.die.net/man/1/tree

## `tree -I node_module`: 特定ディレクトリを省いて tree 表示したい


例

```bash
# javascript なら
tree -I node_module

# golang なら
tree -I vendor
```

tree(1) - Linux man page  
https://linux.die.net/man/1/tree

> -I pattern
>     Do not list those files that match the wild-card pattern. 

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

# hugo

The world’s fastest framework for building websites | Hugo  
https://gohugo.io/

## `hugo`: static page のビルド

hugo | Hugo  
https://gohugo.io/commands/hugo/

```bash
$ hugo
```

諸事情によってビルド結果を手動でデプロイしたい場合に使える

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

## footnote: 脚注、補足説明、注釈、下記

footnoteの意味・使い方・読み方 | Weblio英和辞書  
https://ejje.weblio.jp/content/footnote

> in a footnote 脚注に

> in footnote 3 脚注 3 で

> a footnote by the author 作者自身つけた注釈

> See the footnote on page 5. 5ページ下記を参照してください

## Even if: たとえ

Even ifの意味・使い方・読み方 | Weblio英和辞書  
https://ejje.weblio.jp/content/Even+if

> Even if I try taking ... を取ってみても

> Even if that were the case そうであったとしても

## evicted: 立ち退かせる、追い立てる

evictedの意味・使い方 - 英和辞典 WEBLIO辞書  
https://ejje.weblio.jp/content/evicted

> He was evicted for non-payment of rent. 彼は家賃を払わないために家を立ち退かせられた

> To provide a mechanism for determining which data is to be evicted in the first place from an intermediate cache such as an L2 cache. Ｌ２キャッシュなどの中間キャッシュからどのデータをまずエビクトすべきかを判定する機構を提供する。

## dip: 浸す、すくい上げる、少し下げる

英語「dip」の意味・使い方・読み方 | Weblio英和辞書  
https://ejje.weblio.jp/content/dip

> dip a towel (in) タオルをちょっと浸す.

> dip hot water out of a pot なべから湯をくみ出す.

> dip a curtsy 軽くひざを曲げて会釈する.

## referred: 言及する、触れる、引き合いに出す

referredの意味・使い方 - 英和辞典 WEBLIO辞書  
https://ejje.weblio.jp/content/referred

> a referred example 引用した例

## callout: ... を大声で呼ぶ、 ... を呼び出す、出勤させる、喧嘩を挑む、発呼

calloutの意味・使い方・読み方 | Weblio英和辞書  
https://ejje.weblio.jp/content/callout

> to call out to someone. (人に)話しかける

## 夏時間: Daylight Savings Time, Suumer Time

Daylight Savings Timeの意味・使い方 - 英和辞典 WEBLIO辞書  
https://ejje.weblio.jp/content/Daylight+Savings+Time

> 現地標準時間より時計を1時間進めた時間

> I hear that the daylight savings time system is popular overseas. 海外ではサマータイム制度が盛んだと聞いている。

> The clock was set ahead one hour for Daylight Savings Time. その時計は夏時間のために1時間進められた

## glance: 一見、チラ見、きらめき

glanceの意味・使い方・読み方 | Weblio英和辞書  
https://ejje.weblio.jp/content/glance

> give [shoot] a person a glance 人をちらりと見る.

> I glanced at my wrist watch. ちょっと腕時計を見た.

> The old man glanced at the boy. 老人は少年をちらっと見た

> He glanced through the newspaper. 彼は新聞にざっと目を通した

## significant: 重要な、意味深な、かなりの

significant とは 意味・読み方・表現 | Weblio英和辞書  
https://ejje.weblio.jp/content/significant

> a significant date 重要な日 《記念日など》.

> a significant phrase 意義深い語句.

## steep: 急な、激しい、大げさな、険しい、法外な、途方もなく高い

steep とは 意味・読み方・表現 | Weblio英和辞書  
https://ejje.weblio.jp/content/steep

steep discounts 大幅な割引

## Dedicated: 専用の、特定の目的のための、献身的な

Dedicated とは 意味・読み方・表現 | Weblio英和辞書  
https://ejje.weblio.jp/content/Dedicated

> a dedicated line 専用回線

> a dedicated server 専用サーバー

> Dedicated to ... (本書を) ... に捧ぐ

## Differentiate: 区別する、識別する、差異を生じさせる

英語「Differentiate」の意味・使い方・読み方 | Weblio英和辞書  
https://ejje.weblio.jp/content/Differentiate

> differentiate these two plants これら二つの植物を識別する.

> differentiate a rat from a mouse ネズミとハツカネズミを区別する.

> How do you differentiate brands in your company? 御社ではどのようにブランド差別化を図っているのですか？

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

## CORS な API をテストできるサイト

Reqres - A hosted REST-API ready to respond to your AJAX requests  
https://reqres.in/

## markdown の table ジェネレーター

Markdown Tables generator - TablesGenerator.com  
https://www.tablesgenerator.com/markdown_tables

File の Paste table data からテーブルテキストをペーストして markdown table を生成してくれる

## JSON を diff できるサイト

JsonDiffPatch  
https://benjamine.github.io/jsondiffpatch/demo/index.html

## JSON を良い感じに見れる Viewer

Online JSON Viewer  
http://jsonviewer.stack.hu/

デベロッパーツールをみた感じ JSON データを通信している感じもない

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

# 便利なツール

## iOS, Android といったモバイルデバイスの通信状況を確認したい

Charles Web Debugging Proxy • HTTP Monitor / HTTP Proxy / HTTPS & SSL Proxy / Reverse Proxy  
https://www.charlesproxy.com/

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

## AWS Encryption SDK

What Is the AWS Encryption SDK? - AWS Encryption SDK  
https://docs.aws.amazon.com/encryption-sdk/latest/developer-guide/introduction.html

awslabs/aws-encryption-sdk-specification: AWS Encryption SDK Specification  
https://github.com/awslabs/aws-encryption-sdk-specification

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

ECMAScript® 2019 Language Specification
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

YAML™ Specification Index
https://yaml.org/spec/

yaml/yaml: YAML language and community information
https://github.com/yaml/yaml

YAML Ain’t Markup Language (YAML™) Version 1.2
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


## CPython

python/cpython: The Python programming language  
https://github.com/python/cpython

## Java

Java SE Specifications  
https://docs.oracle.com/javase/specs/

## WebSocket

RFC 6455 - The WebSocket Protocol  
https://tools.ietf.org/html/rfc6455
