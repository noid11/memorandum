何度も調べたくない事の備忘録。

<!-- TOC -->

- [Visual Studio Code](#visual-studio-code)
    - [Markdown TOC](#markdown-toc)
    - [`Command + Shift + O`: Markdown の見出しをベースに移動できる](#command--shift--o-markdown-の見出しをベースに移動できる)
    - [ショートカット一覧](#ショートカット一覧)
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
- [`wc`](#wc)
    - [`echo -e '1\n2\n3' | wc -l`: 行数をカウントしたい](#echo--e-1\n2\n3--wc--l-行数をカウントしたい)
    - [`pbpaste | wc -w`: クリップボードにコピーした文字列の長さを知りたい](#pbpaste--wc--w-クリップボードにコピーした文字列の長さを知りたい)
- [`cut`: 受け取った文字列を分割して扱いたい](#cut-受け取った文字列を分割して扱いたい)
- [パフォーマンス系](#パフォーマンス系)
    - [CPU 使用率を上げたい](#cpu-使用率を上げたい)
- [Git](#git)
    - [直前の commit 取り消し](#直前の-commit-取り消し)
    - [ファイルやディレクトリのリネーム](#ファイルやディレクトリのリネーム)
    - [プライベートな GitHub アカウントで使ってる Git ユーザーを設定する](#プライベートな-github-アカウントで使ってる-git-ユーザーを設定する)
- [AWS CLI](#aws-cli)
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
- [one liner](#one-liner)
    - [`while`](#while)
    - [`for`](#for)
- [便利な Web サイト](#便利な-web-サイト)
    - [自分のグローバル IP を知りたい、特定の IP アドレスの位置情報とか調べたい](#自分のグローバル-ip-を知りたい特定の-ip-アドレスの位置情報とか調べたい)
        - [ipinfo.io](#ipinfoio)
        - [checkip](#checkip)
    - [GiB, MiB 等の単位変換](#gib-mib-等の単位変換)
    - [CIDR 範囲調べたい](#cidr-範囲調べたい)
- [仕様とかリファレンスとか](#仕様とかリファレンスとか)
    - [AWS Guides and API Reference](#aws-guides-and-api-reference)
    - [AWS CLI Reference](#aws-cli-reference)
    - [CloudFormation](#cloudformation)
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

<!-- /TOC -->

# Visual Studio Code

Documentation for Visual Studio Code
https://code.visualstudio.com/docs

## Markdown TOC

Auto Markdown TOC が日本語見出しにも対応してて良い感じ

Auto Markdown TOC - Visual Studio Marketplace
https://marketplace.visualstudio.com/items?itemName=huntertran.auto-markdown-toc

## `Command + Shift + O`: Markdown の見出しをベースに移動できる

便利

## ショートカット一覧

Visual Studio Code Key Bindings
https://code.visualstudio.com/docs/getstarted/keybindings#_keyboard-shortcuts-reference

keyboard-shortcuts-macos.pdf
https://code.visualstudio.com/shortcuts/keyboard-shortcuts-macos.pdf

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

# パフォーマンス系

## CPU 使用率を上げたい

```bash
yes > /dev/null &
```

# Git

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
```

`user.email` に設定するメアドは https://github.com/settings/emails を確認する。


# AWS CLI

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

# one liner

## `while`

```bash
 while sleep 1; do date; done
```

## `for`

```bash
$ for i in {1..5}; do echo $i; done
$ for ( ; ; ); do date; done
```

# 便利な Web サイト

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

# 仕様とかリファレンスとか

## AWS Guides and API Reference

AWS Documentation
https://docs.aws.amazon.com/

サービスのユーザーガイドとか、開発者ガイドとか、API リファレンスとか、チュートリアルとか。

## AWS CLI Reference

AWS CLI Command Reference
https://docs.aws.amazon.com/cli/latest/index.html

## CloudFormation

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
