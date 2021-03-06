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

実行コンテキストが生成されたら、JSエンジンんは実行に必要なオブジェクトを生成する。

#### これを　Variable Object　 (VO / 変数オブジェクト)という。

Variable Objectはコードが実行されるとき、エンジンによって参照され、コードでは接近ができない

```
変数
parameter　、　arguments
関数宣言（関数表現式は除外）
```

<!--
Variable Object는 실행 컨텍스트의 프로퍼티이기 때문에 값을 갖는데 이 값은 다른 객체를 가리킨다. 그런데 전역 코드 실행시 생성되는 전역 컨텍스트의 경우와 함수를 실행할 때 생성되는 함수 컨텍스트의 경우, 가리키는 객체가 다르다. 이는 전역 코드와 함수의 내용이 다르기 때문이다. 예를 들어 전역 코드에는 매개변수가 없지만 함수에는 매개변수가 있다.

Variable Object가 가리키는 객체는 아래와 같다.
-->

### 2. Scope Chain (SC)

### 3. this value

## 実行コンテキストの生成流れ

