# ブラウザでgoogle.comに接続したら起きること。

* https://devjin-blog.com/what-happen-browser-search/
* https://medium.com/@maneesha.wijesinghe1/what-happens-when-you-type-an-url-in-the-browser-and-press-enter-bb0aa2449c1a

ブラウザの動きは知ってるか、細かく説明してるブログがあるので記入してみる

## 0. google.comをブラウザに入力。

## 1. ブラウザはキャッシングされたDNS記録をみてgoogle.comのIPアドレスが存在するかを確認する

* DNSにはURL名とIPアドレスを保存してる。URLにはフォワディングされてるIPアドレスが存在する。

1. <b>ブラウザ</b> ブラウザのキャシングを確認する。ブラウザにはユーザーが設定した期間のDNS記録が保存されてる。
2. <b>OS</b> ブラウザキャシングにIPアドレスが存在してないなら、OSが保存してるDNS記録を確認する。
3. <b>router</b> 次はrouterキャシングを確認する。routerにもDNS記録をキャシングしてる。
4. <b>ISP</b> それでもなかったらISPキャシングを確認する。ISPはDNSサーバーを構築してるので、ブラウザが最後に確認する場所である。

* キャシングを保存、キャシングを最初に確認する理由はネットワークトラフィックの調節、データー送信時間を短くするため
* ブラウザがキャシングを確認するでまとめてOK

## 2. ISPのDNSサーバーがgoogle.comをホスティングしてるサーバーを探すため、DNS queryを送信する

* DNS queryの目的は他のDNSサーバーを検索して、該当サイトのIPアドレスを探すこと。これをrecursive searchという
* 他のDNSサーバーにqueryを送って、該当URLのIPアドレスがなくてエラーが発生するまでIPアドレスを探す

<!-- TODO: name serverの動きは別でまとめる -->

## 3. IPアドレス取得後、サーバーとTCPコネクションする

* IPアドレスの確認ができたので、サーバーとTCPconnectionをビルドする（HTTPリクエストがTCPのため）

クライアントとサーバーを連結するため、TCP connection(TCP/IP three-way handshake)を行う

1. クライアントがSYNパケットを送信してconnectionリクエストする
2. サーバーが新しいconnection　ポートがあればSYN/ACKパケットで返事を送る
3. クライアントがSYN/ACKパケットを受けたら、サーバーにACKパケットを送信する

## 4.　ブラウザがサーバーにHTTPリクエストする

* TCPで連結済みなので、データー送信が始まる
* HTTPメソッドによるGET/POST/PUT...
 
1. browser identification(User-Agent Header)
1. リクエストの種類(Accept Header)
1. 追加リクエストのため、TCP connection維持リクエストのことが書いてるconnectionヘッダー
1. ブラウザのクッキ情報
1. その他

## 5. サーバーがリクエストを処理してresponseを生成する

responseを生成するのはRequest Handler（JAVA、PHP、Rubyみたいなプログラミング言語で作成されたもの）が行う。

<!-- TODO: Request Handlerの動き（EX:JAVA Spring Boot）は別でまとめる -->

## 6. HTTP responseを送信する

<!-- TODO: HTTP responseについては別でまとめる -->

## 7. ブラウザがHTML contentを表示する

<!-- TODO: ブラウザの表示動きについては別でまとめる -->

ブラウザはHTML contentを段階的に表示する。

1. HTML 枠レンダリング
2. HTML tagをチェックして追加で必要はファイルをGETでリクエストする（キャシング対象になる）


