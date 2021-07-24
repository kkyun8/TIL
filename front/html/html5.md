# なぜHTML5なのか？

* 登場背景：HTMLで単純な操作ではなく、様々な機能を使いたい

Multimedia, Graphics, Device acess, Semantics, Storage, CSS3...　HTML5の登場でWEBブラウザをもっと活用できる。

## HTML DOM & NODE

抽象的に認識してたのでまとめてみた

* HTML DOMは「Node」という親子構造に情報を保存してる
  * HTMLをjavascriptが操作・理解できるようにするため、登場したのがDOM  
* HTML DOMはこういう「Node」を定義し、関係を説明する役割をする。
* HTMLの中の階層のことを「Node Tree」という

## Semantic Webとは

* エンジニアが作成した要素の意味が明確にわかるように作成する方法。
* ブラウザー、検索エンジン、エンジニアみんなにコンテンツの意味を明確に説明する役割

よりわかりやすいコードになるし、SEOWebの検索エンジンの最適化であるWebが作れる。

* 登場背景：Webの検索エンジンの最適化のため
  * EX：検索エンジンのクローラーではh1タグをタイトルで認識するので、div、pなどのタグではなくタイトルを作成せずh1タグにすること
 
 
HTML要素はnon-semantic要素、semantic要素に区別できる
* non-semantic
  * div, span... <b>contentについて説明しない</b>
* semantic
  * form, table, img... <b>contentの意味を明確に説明する</b>
* HTML5で追加されたsemantic
  * header, nav, aside, section, article, footer
