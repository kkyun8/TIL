# Junit repository test

SpringBootでUnitテストの中でRepositoryテストについてまとめ。

## SQLはどうやってテストするのか？

バックエンドでSQLのUnitテストは、Migration機能がちょっとめんどくさいSpringBootだとどういう方法があるのかまとめてみた。

結論から言うと、DbUnitを使うか、SpringBootでモックデータを作って、Repositoryが正常に動作するのか確認ができる

https://techblog.woowahan.com/2650/


## 現場ではDBunitを使ってた

DB Unitを使うと、Junitが起動する際にモックデーターをDBに保存することができるので便利。

モックデーターはSpringプロジェクトでXMLファイルで管理されるし、Junit実行前に作成→完了後DB削除などもトランザクションも可能。

## やっぱりなんかめんどくさい感じ。。

Rails、LaravelだとMigrationコードで簡単にモックデーターを作ってUnitテストが可能なので、、、わざわざDBunit設定などをするのはまだ慣れてない。。


