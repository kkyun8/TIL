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
