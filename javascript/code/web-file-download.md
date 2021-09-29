# Responseに含まれてるファイルをブラウザーでダウンロード表示する方法
 
```javascript
// set param
const params = new URLSearchParams();
params.append('id', 1);
params.append('token', this.token);

await axios.get('/get', params, {
 responseType: 'blob', // レスポンスタイプ設定（設定しないとファイルBLOB変換が正しくできない）
}).then((response) => {
 const blob = response.data;
 // createElement
 const link = document.createElement('a');
 
 // response data -> createObjectURL
 link.href = window.URL.createObjectURL(blob);
 
 // ファイル名設定、普段レスポンスに含まれてるファイル名で設定
 link.download = 'file';
 
 // ブラウザーでダウンロード
 link.click();
})
```
## BLOBのURLをメモリ上で削除する


ダウンロード用のURLなので、またURLを使うことはない。URLがメモリに残ってしまうので、即時削除する。


```javascript
.
.
.
 // response data -> createObjectURL
 link.href = window.URL.createObjectURL(blob);
 
 // ファイル名設定、普段レスポンスに含まれてるファイル名で設定
 link.download = 'file';
 
 // ブラウザーでダウンロード
 link.click();
 
 // ブラウザーメモリでURLを削除
 URL.revokeObjectURL(link.href)
})
.
.
.
```
