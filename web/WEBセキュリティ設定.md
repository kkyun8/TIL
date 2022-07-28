# WEB（HTTP）セキュリティ設定

WEBのセキュリティー対策に必要な設定についてまとめ

## WEB を HTTPS が対応できるようにする

HTTPSは「このサイトは安全だと認定されました」という証明。オープンサイトなら必ずHTTPS対応しよう。

HTTP を HTTPS に変更するのは「SSL 証明書」の発行必要。

### HTTPSが使えるようになったら、HTTPに接続した場合、リダイレクトで HTTPSに遷移する機能 Strict-Transport-Securityを設定

* https://developer.mozilla.org/ja/docs/Web/HTTP/Headers/Strict-Transport-Security


## Header設定

### Access-Control-Allow-Methods

通信可能なHTTPメソッドを制御する
* https://developer.mozilla.org/ja/docs/Web/HTTP/Headers/Access-Control-Allow-Methods

### X-XSS-Protection（XSSフィルター機能）

クロスサイトスクリプティング (XSS) 攻撃を検出したときに、ページの読み込みを停止するためのもの。

* https://developer.mozilla.org/ja/docs/Web/HTTP/Headers/X-XSS-Protection
* https://developer.mozilla.org/ja/docs/Glossary/Cross-site_scripting

### Content-Security-Policy(CSP)

ウェブサイトが通信するサーバー制御する。（script、img、mediaなどウェブサイトが参照するURLを指定）

* https://developer.mozilla.org/ja/docs/Web/HTTP/CSP
* https://content-security-policy.com/
