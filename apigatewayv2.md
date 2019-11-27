# API Gateway WebSocket メモ

# TOC

<!-- TOC -->

- [API Gateway WebSocket メモ](#api-gateway-websocket-メモ)
- [TOC](#toc)
- [docs](#docs)
- [ドキュメント読んだメモ](#ドキュメント読んだメモ)
- [CloudFormation](#cloudformation)
- [Glossary](#glossary)
    - [API](#api)
        - [routeSelectionExpression](#routeselectionexpression)
        - [apiKeySelectionExpression](#apikeyselectionexpression)
        - [disableSchemaValidation](#disableschemavalidation)
        - [warnings](#warnings)
        - [apiEndpoint](#apiendpoint)
    - [ルート](#ルート)
        - [ModelSelectionExpression](#modelselectionexpression)
        - [OperationName](#operationname)
        - [RequestModels](#requestmodels)
        - [RequestParameters](#requestparameters)
        - [RouteKey](#routekey)
        - [RouteResponseSelectionExpression](#routeresponseselectionexpression)
        - [Target](#target)
    - [Integration](#integration)
        - [IntegrationType](#integrationtype)
        - [templateSelectionExpression](#templateselectionexpression)
        - [passthroughBehavior](#passthroughbehavior)
        - [contentHandlingStrategy](#contenthandlingstrategy)
    - [IntegrationReponse](#integrationreponse)

<!-- /TOC -->

# docs

Amazon API Gateway での WebSocket API の作成、デプロイ、および呼び出し - Amazon API Gateway  
https://docs.aws.amazon.com/ja_jp/apigateway/latest/developerguide/apigateway-websocket-api.html

Amazon API Gateway Version 2 API Reference - Amazon API Gateway  
https://docs.aws.amazon.com/apigatewayv2/latest/api-reference/api-reference.html

apigatewayv2 — AWS CLI 1.16.290 Command Reference  
https://docs.aws.amazon.com/cli/latest/reference/apigatewayv2/index.html

Amazon API Gateway V2 リソースタイプのリファレンス - AWS CloudFormation  
https://docs.aws.amazon.com/ja_jp/AWSCloudFormation/latest/UserGuide/AWS_ApiGatewayV2.html

# ドキュメント読んだメモ

- WebSocket API では受信する JSON メッセージは設定したルートに基づいてバックエンド統合に転送される
    - JSON 以外のメッセージは設定した `$default` ルートに転送される
- ルートにはルートキーが含まれる
    - これはルート選択式が評価された時に予期される値
    - 属性 routeSelectionExpression は、 API レベルで定義される
    - メッセージペイロードに存在することが予期される JSON プロパティを指定する
- JSON メッセージに action プロパティが含まれていて、このプロパティに基づいて様々なアクションを実行する場合、ルート選択式は `${request.body.action}` のようになる
    - ルーティングテーブルでは、このテーブルで定義したカスタムルートキーの値に対して action プロパティの値を一致させることによって、実行するアクションを指定する
- 事前定義されたルート
    1. `$connect`
        - クライアントは WebSocket アップグレードリクエストを送信して WebSocket API に接続する
        - クライアントと WebSocket API 間の永続的な接続が開始された時に呼び出される
        - WebSocket はステートフルな接続であるため、 `$connect` ルートのみ認証を設定できる。 AuthN/AuthZ は接続時のみ実行される
        - `$connect` ルートに関連付けれられている統合の実行が完了するまでに、アップグレードリクエストは保留中となり、実際の接続は確立されない
            - AuthN/AuthZ の障害や、統合の障害等によって `$connect` リクエストが失敗した場合、接続は行われない
            - `$connect` で承認が失敗した場合、接続は確立されず、クライアントは 401, 403 レスポンスを受け取る
        - `$connect` の統合の設定はオプション
            - ただし、バックエンドは接続するクライアントのユーザー ID を受け取るため、この操作を行うと有効
            - 次の場合は `$connect` 統合の設定を検討
                - クライントが接続および切断した時に通知を受けたい
                - 接続をスロットリングしたい。接続するユーザーを管理したい
                - バックエンドで、コールバック URL を使用してメッセージをクライアントに送信したい
                - 各接続 ID および、その他の情報をデータベースに保存したい
    2. `$disconnect`
        - クライアントまたはサーバーが API から切断した時に呼び出される
        - 正確には、接続を閉じた後に実行される
        - 接続は、サーバーまたはクライアントによって閉じることが可能
            - `$disconnect` 実行しには接続が既にクローズしているため、 `$disconnect` はベストエフォート型のイベント
            - API Gateway は統合に `$disconnect` イベントを配信するために最善を尽くしますが、配信は保証しない
        - バックエンドは `@connections` API を使用して切断を開始できる
    3. `$default`
        - ルート選択式をメッセージに対して評価できない場合や、一致するルートが見つからない場合に呼び出される
        - 定義されたルートキーと一緒に使用
            - 定義されたキーと一致しない受信メッセージの「フォールバック」ルートとして使える
            - 特定のエラーメッセージを返す汎用モック統合
        - 定義されたルートキーなしで使用
            - バックエンドコンポーネントにルーティングを委任するプロキシモデルを指定できる
        - JSON 以外のペイロードのルートを指定できる
- カスタムルート
    - 一致するルートが見つかった場合、メッセージに対してルート選択式が評価された後でカスタムルートが呼び出される
    - この一致により、呼び出される統合が決まる
    - メッセージの内容に基づいて特定の統合を呼び出す場合、カスタムルートを作成して行う
    - カスタムルートは指定されたルートキーと統合を使用する
        - 受信メッセージに JSON プロパティがが含まれていて、そのプロパティがルートキーの値に一致する値に評価される場合、 API Gateway は統合を呼び出す
- ルートを使用したメッセージ処理
    - メッセージ内容に基づいて JSON メッセージをルーティングし、特定のバックエンドサービスを実行できる
    - クライアントが WebSocket 接続経由でメッセージを送信すると、これが WebSocket API に対するルートリクエストになる
    - リクエストが API Gateway の対応するルートキーを持つルートと照合される
        - マネジメントコンソールは統合の再利用をサポートしていないため、最初にルートを作成してからルート統合を作成する必要がある
    - 統合リクエストに進める前にルートリクエストの検証を実行するよう API Gateway を設定できる
        - 検証に失敗すると API Gateway がバックエンドへのリクエストを行わずにクライアントにエラーを返す
            - これによってバックエンドへの不要な呼び出しが減り、 API その他の要件に集中できる
    - API のルートに対するルートのレスポンスを定義し、双方向通信を有効化することもできる
        - ルートレスポンスは、特定のルートの統合完了時に、どのようなデータがクライントに送信されるかを示す
        - クライアントがレスポンスを受信せずにバックエンドにレスポンスを送信するような場合(単方向通信)、ルートのレスポンスを定義する必要はない
        - ルートレスポンスのルートを提供しない場合、 API Gateway は統合の結果に関する情報をクライアントに送信しない
- REST API との相違点
    - マネジメントコンソールでは、最初にルートを作成してから、そのルートのターゲットとして統合を作成する必要がある
        - API, CLI を使用する場合、ルートと統合を任意の順序で個別に作成できる
    - 複数のルートに単一の統合を使用できる
        - 相互に密接に関連した一連のアクションがある場合、それら全てのルートを単一の Lambda 関数で動かしたいとか
            - こういった場合、統合の詳細を複数回定義する代わりに1回指定し、関連する各ルートに割り当てることができる
    - API Gateway は、ルートと統合で使用できる複数の選択式を提供する
        - 入力テンプレートまたは出力マッピングを選択するために、コンテンツタイプに依存する必要はない
        - ルート選択式の場合と同じく、 API Gateway で評価される選択式を定義して、適切な項目を選択できる
            - これら全ては一致するテンプレートが見つからない場合に、 `$default` テンプレートにフォールバックされる
        - 統合リクエストでテンプレート選択式は `$request.body.<json_path_expression>` および静的な値をサポートしている
        - 統合レスポンスでテンプレート選択式は `$request.body.<json_path_expression>`, `$integration.response.statuscode`, `$integration.response.header.<headerName>` をサポートしている
    - AWS_PROXY, LAMBDA_PROXY 統合を使用するように設定されたルートでは、通信は一方向で、 API Gateway は自動的にルートレスポンスにバックエンドレスポンスをパススルーしない
        - たとえば、 LAMBDA_PROXY 統合の場合は、 Lambda 関数が返す本文はクライアントに返されない
        - クライントが統合レスポンスを受信するには、ルートレスポンスを定義して、双方向通信を可能にする必要がある
    - バイナリペイロードの処理
        - WebSocket API は受信メッセージをペイロードでバイナリフレームをサポートしていない
            - クライアントアプリがバイナリフレームを送信した場合、 API Gateway はこれを拒否し、 1003 コードでクライアントを切断する
        - 回避策
            - クライアントがテキストでエンコードされたバイナリデータ(Base64 など)をテキストフレームとして送信する場合、統合の contentHandlingStrategy プロパティを CONVERT_TO_BINARY に設定して、ペイロードを Base64 エンコードの文字列からバイナリに変換できる
        - プロキシ以外の統合でバイナリペイロードのルートレスポンスを返すには、統合レスポンスの contentHandlingStrategy プロパティを CONVERT_TO_TEXT に設定して、ペイロードをバイナリから Base64 でエンコードされた文字列に変換できる

# CloudFormation

AWS::ApiGatewayV2::Api - AWS CloudFormation  
https://docs.aws.amazon.com/ja_jp/AWSCloudFormation/latest/UserGuide/aws-resource-apigatewayv2-api.html


# Glossary

## API

WebSocket API のこと

Apis - Amazon API Gateway
https://docs.aws.amazon.com/ja_jp/apigatewayv2/latest/api-reference/apis.html

### routeSelectionExpression

ルート選択式のこと。
メッセージペイロードに存在することが予期される JSON プロパティを指定する。

`$request.body.action` みたいな値を指定する

この場合、ルーティングテーブルでは、テーブルで定義したカスタムルートキーの値に対して、 action プロパティの値を一致することによって実行するアクションを指定する。

例えば以下のような JSON メッセージを受信する場合、、、

```json
{
    "service" : "chat",
    "action" : "join",
    "data" : {
        "room" : "room1234"
   }
}
```

action は join として評価される。

API Gateway の WebSocket 選択式 - Amazon API Gateway
https://docs.aws.amazon.com/ja_jp/apigateway/latest/developerguide/apigateway-websocket-api-selection-expressions.html#apigateway-websocket-api-route-selection-expressions

これは JSONPath 式として評価されるので、結果は文字列化される。
JSON の値として配列やオブジェクトが指定される場合でも、それらは文字列として解釈される。

ルート選択式では JSONPath を使用せずに静的な値を指定することもできるし、複数の変数を使用することもできる

- `$request.body.action`
    - join
    - 1つのラップ解除された変数
- `${request.body.action}`
    - join
    - 1つのラップされた変数
- `${request.body.service}/${request.body.action}`
    - chat/json
    - 静的な値を持つ複数の変数
- `${request.body.action}-${request.body.invalidPath}`
    - join
    - JSONPath が見つからない場合、変数は "" として解決される
- `action`
    - action
    - 静的な値
- `\$default`
    - $default
    - 静的な値 $ をエスケープ

### apiKeySelectionExpression

API キー選択式

クライアントが有効な API キーを提供した場合のみ、特定のリクエストを続行する必要があるとサービスが決定した時に評価する

サポートされている値

- `$request.header.x-api-key`
- `$context.authorizer.usageIdentifierKey`

API Gateway の WebSocket 選択式 - Amazon API Gateway
https://docs.aws.amazon.com/ja_jp/apigateway/latest/developerguide/apigateway-websocket-api-selection-expressions.html#apigateway-websocket-api-apikey-selection-expressions

### disableSchemaValidation

デプロイメントを作成する際にモデルのバリデーションをするかしないかのフラグ

### warnings

API インポートする時にレポートするのか

### apiEndpoint

API の URI

## ルート

WebSocket API のアクションを決めるリソース。
デフォルトで

1. $connect
2. $disconnect
3. $default

の3つが定義されている。
ユーザーが作成するルートキーに $ を含めることはできない。これは AWS によって予約されたプレフィックス

Routes - Amazon API Gateway
https://docs.aws.amazon.com/ja_jp/apigatewayv2/latest/api-reference/apis-apiid-routes.html#apis-apiid-routespost

AWS::ApiGatewayV2::Route - AWS CloudFormation
https://docs.aws.amazon.com/ja_jp/AWSCloudFormation/latest/UserGuide/aws-resource-apigatewayv2-route.html

### ModelSelectionExpression

モデル選択式

リクエストが受信された時にボディの検証に使用するモデルの選択。
ルートの requestmodels のエントリで評価

API Gateway の WebSocket 選択式 - Amazon API Gateway
https://docs.aws.amazon.com/ja_jp/apigateway/latest/developerguide/apigateway-websocket-api-selection-expressions.html#apigateway-websocket-api-model-selection-expressions

### OperationName

オペレーション名。これは RouteKey とは異なるので注意。
オプショナルなので無い場合もある。

### RequestModels

モデル選択式で使うモデル

### RequestParameters

ルートが受け取るリクエストパラメーター

### RouteKey

ルートキー。
$default とかそういうの

### RouteResponseSelectionExpression

ルートレスポンス選択式

バックエンドからクライアントにレスポンスをモデル化するのに使用する。
WebSocket メッセージを受信したときにレスポンスをクライアントに返す必要があることを API に指定。

現状 $default ルートキーのみ対応。

API Gateway の WebSocket 選択式 - Amazon API Gateway
https://docs.aws.amazon.com/ja_jp/apigateway/latest/developerguide/apigateway-websocket-api-selection-expressions.html#apigateway-websocket-api-route-response-selection-expressions

### Target

ルートが連携するインテグレーション
`integrations/[IntegrationId]` のようなフォーマットで指定する。

## Integration

Integrations - Amazon API Gateway
https://docs.aws.amazon.com/ja_jp/apigatewayv2/latest/api-reference/apis-apiid-integrations.html

### IntegrationType

統合タイプ

- AWS
    - Lambda 関数呼び出しアクション等、 AWS サービスアクションとルートまたはメソッドリクエストを統合
    - Lambda 関数呼び出しアクションは特別に Lambda カスタム統合と呼ばれる
    - 他の AWS サービスアクションは AWS 統合と呼ばれる
- AWS_PROXY
    - ルートまたはメソッドリクエストを Lambda 関数呼び出しアクションと統合し、クライアントリクエストをそのまま渡す
    - Lambda プロキシ統合と呼ばれる
- HTTP
    - ルートまたはメソッドリクエストを HTTP エンドポイントと統合
    - HTTP カスタム統合と呼ばれる
- HTTP_PROXY
    - ルートまたはメソッドリクエストを HTTP エンドポイントと統合し、クライアントリクエストをそのまま渡す
    - HTTP プロキシ統合と呼ばれる
- MOCK
    - バックエンドを呼び出さずにルートまたはメソッドリクエストを loopback エンドポイントとして API Gateway と統合

### templateSelectionExpression

テンプレート選択式

統合リクエスト、統合レスポンスを定義する際に使用できるテンプレート選択式。ボディの変換、レスポンスの変換に使用するテンプレートを決定する。

API Gateway の WebSocket 選択式 - Amazon API Gateway
https://docs.aws.amazon.com/ja_jp/apigateway/latest/developerguide/apigateway-websocket-api-selection-expressions.html#apigateway-websocket-api-template-selection-expressions

### passthroughBehavior

リクエストの Content-Type ヘッダー、および Integration リソースの requestTemplates プロパティとして指定された使用可能なマッピングテンプレートに基づいて、受信リクエストのパススルー動作

- WHEN_NO_MATCH は、マッピングされていないコンテンツタイプのリクエスト本文を、変換せずに統合バックエンドに渡します。
- NEVER は、マッピングされていないコンテンツタイプを HTTP 415 Unsupported Media Type レスポンスで拒否します。
- 統合にテンプレートにマップされたコンテンツタイプがない場合、WHEN_NO_TEMPLATES はパススルーを許可します。
    - ただし、少なくとも 1 つのコンテンツタイプが定義されている場合、マッピングされていないコンテンツタイプは同じ HTTP 415 Unsupported Media Type レスポンスで拒否されます。 

### contentHandlingStrategy

レスポンスペイロードのコンテンツタイプの変換を処理する方法を指定します。サポートされている値は CONVERT_TO_BINARY と CONVERT_TO_TEXT で、次のように動作します。

- CONVERT_TO_BINARY: レスポンスペイロードを Base64 でエンコードされた文字列からバイナリ BLOB に変換します。
- CONVERT_TO_TEXT: リレスポンスペイロードをバイナリ BLOB から Base64 でエンコードされた文字列に変換します。

このプロパティが定義されていない場合、レスポンスペイロードはは、統合レスポンスからルートレスポンスまたはメソッドレスポンスに変更せずにパススルーされます。

## IntegrationReponse

統合レスポンス

AWS::ApiGatewayV2::IntegrationResponse - AWS CloudFormation
https://docs.aws.amazon.com/ja_jp/AWSCloudFormation/latest/UserGuide/aws-resource-apigatewayv2-integrationresponse.html

API Gateway で WebSocket API 統合レスポンスを設定する - Amazon API Gateway
https://docs.aws.amazon.com/ja_jp/apigateway/latest/developerguide/apigateway-websocket-api-integration-responses.html

- ルートが双方向通信用に設定されている場合
    - 統合レスポンスにより、返されたメッセージペイロードで変換を設定できる
    - REST API の統合レスポンスと同じ
    - プロキシ統合の場合
        - API Gateway は自動的にバックエンド出力を完全なペイロードとして呼び出し元に渡すため、統合レスポンスは発生しない
    - 非プロキシ統合の場合
        - 少なくとも1つの統合レスポンスを設定する必要がある
            - 明示的な選択が行われなかった場合、いずれかの統合レスポンスがキャッチオールとして機能する事が理想的
                - 統合レスポンスキーとして `$default` を設定するとか
            - 他のいずれの場合も、統合レスポンスキーは正規表現として機能する
                - `/expression/` 形式に従う
        - API Gateway はバックエンドレスポンスの HTTP ステータスコードへの一致を試みる。
            - この場合、統合レスポンスキーは正規表現として機能する
            - 一致が見つからない場合、 `$default` が統合レスポンスとして選択される
        - テンプレート選択式も、同様に正規表現として機能
            - `/2\d\d/`: 成功のレスポンスを受信して変換
            - `/4\d\d/`: 不正なリクエストエラーを受信して変換
            - `$default`: 全ての予期しないレスポンスを受信して変換
- ルートが単方向通信用に設定されている場合
    - 統合レスポンスの設定に関係なく、メッセージ処理後に WebSocket チャネル経由でレスポンスは返されない
