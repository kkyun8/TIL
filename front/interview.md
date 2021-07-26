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

* Javascript Eventについて説明してください。
  * [JavaScript Event](../javascript/event.md)

* Javascript 非同期について説明してください。
  * [JavaScript Async](../javascript/async.md)

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
