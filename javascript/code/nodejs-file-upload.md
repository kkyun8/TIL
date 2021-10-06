# Node.jsに複数ファイルアップロード


HttpPostでアップロード→サーバーで受け取る→サーバー上に保存の例


## フロントJavascriptでファイル送信


```javascript
// front
const params = new FormData();
params.append('files', file1);
params.append('files', file2);
await this.$axios.$post('/face-api', params, {
 headers: {
  'Content-Type': 'multipart/form-data',
 },
});
```

## Nodejsで取得

```javascript
// server
// multerを使えば簡単
import express from "express";
import multer from "multer";

// create dir
const upload = multer({ dest: 'uploads/' })；

// リクエストを受け、multerでファイル保存
app.post("/upload", upload.array("files"), (req, res) => {
 res.send('完了');
});
```
