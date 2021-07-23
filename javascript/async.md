# 非同期処理まとめ

https://joshua1988.github.io/web-development/javascript/javascript-asynchronous-operation/

## 非同期処理とは

* 特定のロジックの実行が終わるまで待たずに、残ってるコードを先に実行すること。

```javascript
// #1
console.log('Hello');
// #2
setTimeout(function() {
	console.log('Bye');
}, 3000);
// #3
console.log('Hello Again');
```

* setTimeoutを待たずに実行するので、1->2->3ではなく、1->3->2になる。


## 非同期通信の問題点、callback

* callbackなら、特定のロジックが終わったら、終わった後のロジック作成ができる。

```javascript
// AJAX
function getData(callbackFunc) {
	$.get('https://domain.com/products/1', function(response) {
		callbackFunc(response); // レスポンスをcallbackFunc()に渡す。
	});
}

getData(function(tableData) {
	console.log(tableData); // $.get()のresponseがtableDataに
});
```

## でも、callbackにも問題がる、callback hell

* 複数の非同期処理にcallbackを使うなら、以下のような読みにくいコードができる。

```javascript
// callback hell　例
$.get('url', function(response) {
	parseValue(response, function(id) {
		auth(id, function(result) {
			display(result, function(text) {
				console.log(text);
			});
		});
	});
});
```

### callback関数を分けることで問題解決。

```javascript
// 関数を分離すると解決できる
function parseValueDone(id) {
	auth(id, authDone);
}
function authDone(result) {
	display(result, displayDone);
}
function displayDone(text) {
	console.log(text);
}
$.get('url', function(response) {
	parseValue(response, parseValueDone);
});
```

## Promiseの登場

### 非同期処理に対応するオブジェクトPromise

* Promise(+ async, await)を活用するとcallbackよりわかりやすいコードが書ける

```javascript
function getData(callback) {
  // new Promise()
  return new Promise(function(resolve, reject) {
    $.get('url/products/1', function(response) {
      // データーを受けたらcallback resolve()に渡す
      resolve(response);
    });
  });
}

// getData()の実行が終わったらthen()が実行される
getData().then(function(tableData) {
  // resolve()の結果
  console.log(tableData);
});
```

https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/Promise

* pending（待機）: 初期状態。成功も失敗もしていません。
* fulfilled（満足）: 処理が成功して完了したことを意味します。
  * resolveを実行した状態 
* rejected（拒絶）: 処理が失敗したことを意味します。
  * rejectを実行した状態

* then以外にエラーが発生した場合のcatchと、処理が完全に終わったら実行するfinallyが存在する


### Promiseを深く使おう

<!-- TODO 例コード作成 -->
  * Promise.all(iterable)
    * すべてのプロミスが解決されるか、拒否されるかするまで待ちます。
    * 返却されたプロミスが解決された場合、解決されたプロミスが、複数のプロミスが含まれる iterable で定義された通りの順番で入った集合配列の値によって解決されます。
    * 拒否された場合は、 iterable の中で拒否された最初のプロミスの理由によって拒否されます。
      * コード例：
  * Promise.allSettled(iterable)
    * べての Promise が完了する (それぞれが解決するか、拒否される) まで待ちます。
    * Promise を返し、これはすべての与えられた Promise が解決または拒否された後で、それぞれの Promise の結果を記述するオブジェクトの配列で解決されます。
      * コード例：
  * Promise.any(iterable)
    * Promise オブジェクトの反復可能オブジェクトを取り、反復可能オブジェクトの中のプロミスのうちの一つが満足され次第、そのプロミスから受け取った値で解決する単一のプロミスを返します。
      * コード例：
  * Promise.race(iterable)
    * Promise のうちの1つが解決または拒否されるまで待ちます。
    * 返された Promise が解決された場合、 iterable の中で最初に解決された Promise の値によって解決されます。
    * 拒否された場合、最初に拒否された Promise の理由によって拒否されます。
      * コード例：
