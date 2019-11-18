# JavaScript 勉強メモ

# TOC

<!-- TOC -->

- [JavaScript 勉強メモ](#javascript-勉強メモ)
- [TOC](#toc)
- [仕様: ECMAScript](#仕様-ecmascript)
- [リンク](#リンク)
- [アロー関数](#アロー関数)
- [非同期処理あれこれ](#非同期処理あれこれ)
    - [callback って何？](#callback-って何)
    - [Promise って何？](#promise-って何)
    - [aync, await って何？](#aync-await-って何)
        - [async](#async)
        - [await](#await)

<!-- /TOC -->

# 仕様: ECMAScript

ECMAScript® 2020 Language Specification  
https://tc39.es/ecma262/

# リンク

JavaScript | MDN  
https://developer.mozilla.org/ja/docs/Web/JavaScript

この書籍について · JavaScript Primer #jsprimer  
https://jsprimer.net/

とほほのJavaScriptリファレンス  
http://www.tohoho-web.com/js/

# アロー関数

アロー関数 - JavaScript | MDN
https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Functions/Arrow_functions

> アロー関数式は、より短く記述できる、通常の function 式の代替構文

```js
(param1, param2, …, paramN) => { statements } 
(param1, param2, …, paramN) => expression
// 上記の式は、次の式と同等です: => { return expression; }

// 引数が 1 つしかない場合、丸括弧 () の使用は任意です:
(singleParam) => { statements }
singleParam => { statements }

// 引数がない場合、丸括弧を書かねばいけません:
() => { statements }
```

> 2 つの理由から、アロー関数が導入されました。1 つ目の理由は関数を短く書きたいということで、2 つ目の理由は this を束縛したくない、ということです。

# 非同期処理あれこれ

## callback って何？

Callback function (コールバック関数) - MDN Web Docs 用語集: ウェブ関連用語の定義 | MDN  
https://developer.mozilla.org/ja/docs/Glossary/Callback_function

> コールバック関数は他の関数に引数として渡される関数で、外側の関数で何らかの処理やアクションを実行します。

コード例

```js
function greeting(name) {
  console.log('Hello ' + name);
}

function processUserInput(callback) {
  var name = 'john';
  callback(name);
}

processUserInput(greeting);
```

実行例

```bash
$ node
> function greeting(name) {
...   console.log('Hello ' + name);
... }
undefined
> 
> function processUserInput(callback) {
...   var name = 'john';
...   callback(name);
... }
undefined
> 
> processUserInput(greeting);
Hello john
undefined
```

`processUserInput` の引数として関数 `greeting` を指定。
`processUserInput` が呼ばれて、変数 `name` が指定されてから `greeting` が呼び出される。

これは同期コールバックだが、非同期に動作するコールバックもある。

## Promise って何？

Promise - JavaScript | MDN  
https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/Promise

> Promise オブジェクトは非同期処理の最終的な完了処理（もしくは失敗）およびその結果の値を表現します。

> ![promises.png](https://mdn.mozillademos.org/files/15911/promises.png)

Promiseを使う - JavaScript | MDN
https://developer.mozilla.org/ja/docs/Web/JavaScript/Guide/Using_promises

> Promise は非同期処理の最終的な完了もしくは失敗を表すオブジェクト

> 本質的に、Promise はコールバックを関数に渡すかわりに、関数が返したオブジェクトに対してコールバックを登録するようにする、というもの

> Promise オブジェクトは new キーワードとコンストラクターで作成されます。コンストラクターは executor 関数と呼ばれる引数を取ります。 executor 関数は 2 つの関数を引数として取ります。1 つめの関数 (resolve) は非同期タスクが成功して完了した場合に呼び出され、タスクの結果を値として返します。2 つめの関数 (reject) はタスクが失敗した場合に呼び出され、失敗した理由 (典型的には error オブジェクト) を返します。

```js
// これはアロー関数で Promise コンストラクターに指定する関数として、無名関数を作成している
// この無名関数では2つの関数を引数として取る必要があるため、 resolve, reject を指定している。
let myFirstPromise = new Promise((resolve, reject) => {
  setTimeout(function(){
    resolve("Success!"); 
  }, 250);
});

// アロー関数使わない場合の定義
let myFirstPromise = new Promise(function(resolve, reject) {
  setTimeout(function(){
    resolve("Success!"); 
  }, 250);
});

// setTimeout は function, delay sec を引数としてとっているタイマー
// function(){ resolve("Success!") } を 250 ms 後に実行するの意

// .then は Promise オブジェクトが fulfilled(成功), rejected(失敗) どちらの状態になっても呼び出されるハンドラー
// なのでこの場合、 myFirstPromise の状態が何でもいいので変化したら呼び出される。
// で、 .then は2つの引数をとる。 onFulfilled[, onRejected]

// onFulfilled は Promise 成功時に呼び出される関数。 fulfillment value という引数を持つ
// onRejected は Promise 失敗時に呼び出される関数。 rejection reason という引数を持つ

// ここでは .then にアロー関数で無名関数として console.log に Yay! + 渡された文字列を出力する処理を定義している
myFirstPromise.then((successMessage) => {
  console.log("Yay! " + successMessage);
});

// アロー関数使わない場合の定義
myFirstPromise.then(function(successMessage) {
  console.log("Yay! " + successMessage);
});

// 上記の場合 successMessage が onFulfilled として渡される関数で、呼び出され際に fulfillment value を持っている。
// これが Promise 定義時に指定した "Success!" という文字列になる。

```

WindowOrWorkerGlobalScope.setTimeout() - Web API | MDN  
https://developer.mozilla.org/ja/docs/Web/API/WindowTimers/setTimeout

Promise - JavaScript | MDN  
https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/Promise

> pending 状態の Promise は、何らかの値を持つ fulfilled 状態、もしくは何らかの理由 (エラー) を持つ rejected 状態のいずれかに変わります。そのどちらとなっても、then メソッドによって関連付けられたハンドラーが呼ばれます。 (対応するハンドラーがアタッチされたとき、既に Promise が成功または失敗していても、そのハンドラーは呼ばれます。よって、非同期処理とその関連付けられたハンドラーとの競合は発生しません。)

## aync, await って何？

### async

async function - JavaScript | MDN  
https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Statements/async_function

> async function 宣言は、 AsyncFunction オブジェクトを返す 非同期関数 を定義します。非同期関数は非同期でイベントループを介して実行され、暗黙的にPromiseを返します。

Async Function って何？

AsyncFunction - JavaScript | MDN  
https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/AsyncFunction

> AsyncFunction コンストラクターは、新しい async function オブジェクトを生成します。 JavaScript では、すべての非同期関数が実際に AsyncFunction オブジェクトです。

非同期処理:コールバック/Promise/Async Function · JavaScript Primer #jsprimer  
https://jsprimer.net/basic/async/#async-function

> ES2017では、Async Functionという非同期処理を行う関数を定義する構文が導入されました。 Async Functionは通常の関数とは異なり、必ずPromiseインスタンスを返す関数を定義する構文です。

```js
async function doAsync() {
    return "値";
}
// doAsync関数はPromiseを返す
doAsync().then(value => {
    console.log(value); // => "値"
});
```

`new Promise` とか書かずにシンプルに非同期関数を定義できる

> Async Functionではreturnした値の代わりに、Promise.resolve(返り値)のように返り値をラップしたPromiseインスタンスを返します。

```js
// 通常の関数でPromiseインスタンスを返している
function doAsync() {
    return Promise.resolve("値");
}
doAsync().then(value => {
    console.log(value); // => "値"
});
```

### await

await - JavaScript | MDN  
https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Operators/await

> await 演算子は、async function によって Promise が返されるのを待機するために使用します。

非同期処理:コールバック/Promise/Async Function · JavaScript Primer #jsprimer  
https://jsprimer.net/basic/async/#await-expression

> Async Functionの関数内ではawait式を利用できます。 await式は右辺のPromiseインスタンスがFulfilledまたはRejectedになるまでその場で非同期処理の完了を待ちます。 そしてPromiseインスタンスの状態が変わると、次の行の処理を再開します。

asyn function 内で使用できる、非同期処理の完了を待つ構文。

```js
async function asyncMain() {
    // PromiseがFulfilledまたはRejectedとなるまで待つ
    await Promiseインスタンス;
    // Promiseインスタンスの状態が変わったら処理を再開する
}
```

