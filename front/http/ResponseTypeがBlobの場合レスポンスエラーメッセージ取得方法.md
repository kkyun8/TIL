# Response Type が Blob の場合、レスポンスエラーメッセージ取得

## Response Type Blobとは？

mozilla のレスポンスタイプ「BLOB」の説明を参照。

- https://developer.mozilla.org/ja/docs/Web/API/XMLHttpRequest/responseType

```
response はバイナリーデータを含む Blob オブジェクトです。
```

## レスポンスタイプ「BLOB」の場合、レスポンスメッセージを取得できない？

レスポンスタイプが Blob の場合、Blob オブジェクトがレスポンスされるので、一般的なレスポンスタイプである JSON と異なる方法でレスポンスメッセージを取得しないといけない。

```
// 例えばレスポンスタイプ「JSON」で、messageオブジェクトが存在する場合は例外メッセージ取得方法は下記になる。
// しかしレスポンスタイプ「Blob」はこの方法だとメッセージの取得ができず、エラーになる

axios.get().catch((error) => error.response.data.message);
```

その場合に使うのが FetchAPI の text()メソッドである。（Axios も同じ）

## textメソッドでエラーメッセージを取得する。

textメソッドについて
* https://developer.mozilla.org/ja/docs/Web/API/Response/text
* https://ja.javascript.info/fetch
```
response.text()　–　レスポンスをテキストとして返します
```

実行したら（非同期）文字列をリターンする。メッセージを取得したい場合は文字列を JSON.parse して中身を取得する。

<u>JSON.parseできない文字列が存在する場合もあるので注意。</u>

```
const textResult = await err.response.data.text();
 try {
  message = JSON.parse(textResult).message;
 } catch (error) {
  message = textResult;
 }
}
```
