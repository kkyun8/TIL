# Front-end エンジニア　面接質問準備

* 以下のページの内容を日本語でまとめた。~~頭に入ってこない~~
  * https://realmojo.tistory.com/300
  * https://joshua1988.github.io/web-development/interview/frontend-questions/
  * https://velog.io/@honeysuckle/%EC%8B%A0%EC%9E%85-%ED%94%84%EB%A1%A0%ED%8A%B8%EC%97%94%EB%93%9C-%EB%A9%B4%EC%A0%91-%EC%A7%88%EB%AC%B8-%EB%AA%A8%EC%9D%8C
* 追加が必要な内容は自分で追加した。



質問タイプを以下の４つで区分しました。

### 質問タイプ

* よく言われる質問：基本的に知っておく内容
* 実務関連質問：７割ぐらい答えられる内容
* その他の質問：必須ではないか、わかってあればいい内容
* 基本的に準備しないといけない質問：基本的に答えられる内容（準備ができてる内容）

## ★★★★★よく言われる質問：基本的に知っておく内容
* ブラウザーのレンダリングについて詳しく説明してください。（ブラウザの動きについて知ってるものを言ってください。）
  * … [ブラウザでgoogle.comに接続したら起きること。](../cs/what-happens-when-type-google.md)
* ブラウザストレージ（Web Storage）について説明してください。
   * 基本Key、Valueで保存
   * sessionStorage：ページのセッション中(ページの再読み込みや復元を含む、ブラウザーを開いている間) に使用可能な「オリジン　URL」ごとに区切られた保存領域を管理する。
      * 「データー」は「ブラウザ」または「タブ」が閉じられるまで保存される。再読み込みでも保存できる。つまり、「オリジン」でデーター共有はできない。
      * サイズがクッキーより大きい（５MB）
   * localStorage：基本的な動きはsessionStorageと似てるか以下のところが違う。
      * 「有効期限なし」 でデーターを保存する。
      * 「データー」は「ブラウザ」または「OS」が再起動されても保存される。新しいタブで保存データーの確認・変更　ができる、つまり、＊「オリジン」でデーター共有する。
      * サイズがストレージの中で一番大きい
   * localStorageとcookieの違い
      * localStorageはリクエストでサーバーに送信しない。
      * サーバー側がHTTPヘッダーでストレージObjectを操作できない。 
      * localStorageの操作はJS内で制御する。

* Javascript thisについて説明してください。
  * [JavaScript This](../javascript/javascript-this.md)
  * 一般的ににBrowser-siceではwindow、Server-side(Node.js)ではglobalオブジェクト
  * 基本的にGlobalObjectにバインディングされる
    * 例外：objectの内部「関数」のthisは、必ず「Global」になる、親のObjectではない！
  * thisを指摘するために、apply call bindを使おう

* Javascript Eventについて説明してください。
  * [JavaScript Event](../javascript/event.md)

* Javascript 非同期について説明してください。
  * [JavaScript Async](../javascript/async.md)
  * 同期：タスクを順番で処理、非同期：タスクが完了されるまで待たずに、次のタスクを実行
    *　非同期Callback関数の問題点を解決するため、改善するためにPromiseを使う。 

* Javascript クローザーについて説明してください。
  * [JavaScript closure](../javascript/closure.md)
  * 内部関数が、外部関数のコンテキストに接近できることをいう。「外部関数の変数に接近できる内部関数」
  * キャプセル化などができるか、メモリ問題がある

* Javascript Event Loopについて説明してください。
  * [JavaScript Event Loop](../javascript/event-loop.md)
  * （Call Stack）で現在実行中タスクがあるか、実行を待機してるタスク（Event Queue）があるかずっと確認して（Call Stack）が空いてるならEvent Queue → taskを Call Stackに移動し、実行される

* javascript garbage collectionについて説明してください。
  * [JavaScript Garbage Collection](../javascript/garbage-collection.md)　＊未作成
  * 「接近できない」、「到達できない」オブジェクトはGarbageCollectionがメモリ上で削除する
    * GarbageCollectionはエンジンが自動に動く

* javascript var let constの違いは？
  * varとletは変更が可能なオブジェクト、constは変更不可
  * varは「function-scoped」, let・const「block-scoped」
    * let・const「block-scoped」はhoistingが発生しない。２回宣言不可（let i = 1 let i = 1）
    * varはhoisting発生２回宣言可（「i = 1 var i」、「var i = 1 var i = 1」）



## ★★★実務関連質問：７割ぐらい答えられる内容

* フロントエンドビルドシステムについて説明してください。
  * Babel
  * Polyfil
  * Node.js
  * NPM
  * ESlint
  * Prittier
  * Web task manager

* Webpackとは？
* よく使ったJSフレームワークは？
  * Vue.jsと関連した面接質問
    * [Vue.js 質問](../javascript/vue/vuejs-interview.md)
* フロントエンドパフォーマンスチューニングの経験があるのか？
* Virtual DOMについて説明してください。
* CI・CDの経験はありますか？
* Unitテストの経験はありますか？
* Sementicとは？

## ★★★その他の質問：必須ではないか、わかってあればいい内容
* サービスの改善のためやったことは？
* よくわからないAPI、文法があったらどうやって調査するのか
* 他のチームとどうやってやりとりしてるのか
* 仕事で必要な知識を共有した経験はありますか
* 新しく学んだ開発知識はどうやって整理するのか

## 基本的に準備しないといけない質問：基本的に答えられる内容（準備ができてる内容）
* このポジションでエントリーした理由
  * 
* エントリーしたポジションの仕事について調査・理解しましたか？
  * 
* 職務で期待するところと自分が活躍できるとことは？
  * 



<!--
자바스크립트 비동기 처리에 대한 설명
ex) 콜백, 프로미스, async await
ex) 비동기 처리의 특성 및 에러 처리 방법?
프런트엔드 개발은 지속적으로 학습해야 하는 분야인데 어떤식으로 학습을 하고 있는지?

뷰 랜더링 최적화->리랜더링 

실행컨택스트
클로저
이벤트 루프
자바스크립트 원시값
async await 예외처리에 까다로움 
자바스크립트 가비지컬렉션

브라우저랜더링 repainting reflow?
display:none vs ...

..Date객체는 실제시간보다 늦는데 moment를 쓰면 대응할수있다 그이유는?

-->

