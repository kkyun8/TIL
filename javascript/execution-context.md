## 実行コンテキスト

実行コンテキストは(Execution Context)scope, hoisting, this, function, closureなどのJavascriptの実行される環境として定義され流もの。

* グローバルコンテキスト：グローバル　に存在するコード
* Evalコンテキスト：eval関数内の実行されるコード
  * eval関数＞＞https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/eval
* 関数コンテキスト：関数内に存在するコード

一般的実行可能なコードはグローバルと関数である。

Javascript Engineはコードを実行するために実行に必要な情報を知っておかないといけない。

* 実行に必要な情報
  * 変数：グローバル変数、ローカル変数、引数（関数のパラメーター）、オブジェクトのプロパーティー
  * 関数　宣言
  * 変数の有効範囲(Scope)
  * this

```javascript
var x = 'xxx';

function foo () {
  var y = 'yyy';

  function bar () {
    var z = 'zzz';
    console.log(x + y + z);
  }
  bar();
}
foo();
```

上記のコードを実行すると実行コンテキスト”スタック”（Stack）が生成され、消滅する。

現在実行中のコンテスきすで、このコンテキストと関係ないコード（例えば他の関数）が実行されたら「新しいコンテキストが生成」される。

このコンテキストはスタックに重ね、「コントロール（制御権利）」が移動される。


Stack→

|        |        |bar()EC|        |        |
|--------|--------|--------|--------|--------|
|        |foo()EC |foo()EC |foo()EC |        |
|globalEC|globalEC|globalEC|globalEC|globalEC|

1. グローバル　にコントロールが進入すると、グローバルコンテキストが生成され、実行コンテキストに載せされる。グローバル実行コンテキストはアプリケーションが終了（Webページから離れる・ブラウザを閉じる）まで有効。
2. 関数を呼ぶと、該当関数の実行コンテキストが生成され、直前に実行したコードブロックの実行コンテキストの上に載せられる。
3. 関数の実行が終わったら該当関数の実行コンテキストを破棄し、直前の実行コンテキストにコントロール権利が与えられる。


## 実行コンテキストの３つのオブジェクト

### 1. Variable Object (VO / 変数オブジェクト)

### 2. Scope Chain (SC)

### 3. this value

## 実行コンテキストの生成流れ

