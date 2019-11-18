# React.js メモ

# TOC

<!-- TOC -->

- [React.js メモ](#reactjs-メモ)
- [TOC](#toc)
- [リンク](#リンク)
- [JSX](#jsx)
- [props: コンポーネントの再利用に使えるやつ。 read only](#props-コンポーネントの再利用に使えるやつ-read-only)
- [state](#state)

<!-- /TOC -->

# リンク

facebook/react: A declarative, efficient, and flexible JavaScript library for building user interfaces.  
https://github.com/facebook/react

React – A JavaScript library for building user interfaces  
https://reactjs.org/

reactjs/ja.reactjs.org: React documentation website in Japanese
https://github.com/reactjs/ja.reactjs.org/  

React – ユーザインターフェース構築のための JavaScript ライブラリ  
https://ja.reactjs.org/

JSX | XML-like syntax extension to ECMAScript  
https://facebook.github.io/jsx/

facebook/jsx: The JSX specification is a XML-like syntax extension to ECMAScript.  
https://github.com/facebook/jsx

# JSX

JSX | XML-like syntax extension to ECMAScript  
https://facebook.github.io/jsx/

> JSX is an XML-like syntax extension to ECMAScript without any defined semantics.

セマンティクスが定義されていない、 ECMAScript の XML に似たシンタックス拡張

JSX の導入 – React  
https://ja.reactjs.org/docs/introducing-jsx.html

変数踏め込み

```js
const name = 'Josh Perez';
const element = <h1>Hello, {name}</h1>;

ReactDOM.render(
  element,
  document.getElementById('root')
);
```

# props: コンポーネントの再利用に使えるやつ。 read only

コンポーネントと props – React  
https://ja.reactjs.org/docs/components-and-props.html

```js
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}

function App() {
  return (
    <div>
      <Welcome name="Sara" />
      <Welcome name="Cahal" />
      <Welcome name="Edite" />
    </div>
  );
}

ReactDOM.render(
  <App />,
  document.getElementById('root')
);
```

Welcome コンポーネントを複数レンダリングする


# state

state とライフサイクル – React  
https://ja.reactjs.org/docs/state-and-lifecycle.html

