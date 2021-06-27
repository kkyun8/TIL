# ブラウザ動作

chrome、safariみたいなブラウザがどうやって動作するのかまとめ

* ブラウザの基本動きは、レスポンスは利用者が参照したいWebPageをServerにリクエストして、サーバーのレスポンスを受け、ブラウザに表示する・

## レンダリングの動作 Rendering Engineの動き

1. ブラウザはサーバーからHTML,CSS、JSなどをもらう。
1. HTML-> HTMLParseで、DOM Tree　生成
1. HTML ParseがscriptタグがあったらJavascript Engineに制御権限を渡す。
1. Javascript EngineはJSファイルをロードして実行する。実行が終わったら2に戻る
   1. ブラウザは同期的にHTML、CSS、JSを処理する
   1. なのでbodyの一番下にJSを配置するのがいいこと
1. CSS-> CSSParseで、CSSOM Tree生成
1. DOM、CSSOM TreeをRender Treeで結合される
1. Rendering Treeを配置
1. Rendering Tree描画


