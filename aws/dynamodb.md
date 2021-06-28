# DynamoDB

* https://alphahackerhan.tistory.com/39
* https://www.youtube.com/watch?v=DIQVJqiSUkE&feature=youtu.be

* NoSQL・DynamoDBはMysqlのようなRDBMSと概念が全く違う。
* 自分も最初かなり迷ったのでTILにまとめて記入しておく。

## DynamoDBの基本

1. NoSQL、Key:Value概念
1. Primary Keyは Primary Key（重複不可）またはPrimary Key + Sory Key（PKは重複OK,SKは重複不可）で構成される。
1. RDBMSのColumnに該当するのがAttribute。Rowに該当するのがItem。RDBMSと概念が全く違うので、似ているものだと思ったほうがいい。
1. DynamoDBにスキーマがないため、RDBMSのALTER文みたいなものがない。新しいAttributeを持つItemを追加するだけ。

## DynamoDBとRDBS設計の違い

* RDBMS、関係DB管理は効率的なストレージすること。
* NoSQLはストレージが悪くなっても、性能を優先すること。
* RDBMSのJoinはできない。
* Single Table
  * DynamoDBはテーブルを１つにすることができる。むしろ１つにしたほうがQuery性能が良くなる
  * ここでPK・SKの設計がRDBMSと異なる。PKをUSER#、ORDER#みたいにPrefixをつけることで、１つのテーブルで管理が可能

## DynamoDBデーターハンドリング

1. Item-based actions
   1. ItemはRDBMSでRowに該当するもの
   1. 多数のRowを更新することはできない。一回に一アイテム
1. Query
   1. Read-only action、Itemを呼び出すことができるもの。Partition key。
   1. Sort Keyに条件追加可能。Partition + Sort
1. Scan
   1. RDBMSのScanと同一、全てのアイテムをみる機能
   1. Itemが多いなら、重くなる

### Secondary Index

上記の３パタンだと、Query以外に取得できる条件が少ない。
全テーブルを見るScanは性能が良くないので、Secondary Indexを利用する。

## モデルリング（設計）

1. E-commerceサービス
2. ユーザーが注文可能
3. ひとつの注文は複数のアイテムを持つ

### 1. Start with an ERD

RDBMSのようなテーブルの関係を決める

* User : User Address = 1 : N
* User : Order = 1 : N
* Order : Item = 1 : N

### 2. Define your access patterns

どんなアクセルパータンがあるのか？

* ユーザーのプロフィール表示
* ユーザーの全てのオーターを表示
* １つのオーダーとそのオーダーのアイテムを表示
* 一人のユーザーのオーダーステータスを表示
* ユーザーの新規オーダーを表示

### 3. Design your primary keys & secondary indexes

* 1:1、1:N関係をDynamoDBでどうやって表現するのか？

***
#### 1:1

* プロフィールはユーザーの配下概念で、 PK(ユーザー),SK（プロフィール）で表現できる。
* keyの前にPrifix（USER#、#PROFILE#）をつけると、Debug管理でもいいし、重複管理可能。

|PK|SK|Attributes|Attributes|
|------|-----------|----|-----|
|USER#A|#PROFILE#AP|name|email|
|USER#B|#PROFILE#BP|name|email|
|USER#C|#PROFILE#CP|name|email|

***
#### 1:N

1. Attribute (list or map)

* 例えばユーザーとユーザー住所みたいな関係だったら、ユーザー住所だけをアクセスすることはないと思われる。
* 直接アクセルすることがないなら、Attribute化にする
   
2. Primary key + Query

* ユーザーとユーザーのオーダー関係が1:N関係
* オーダー数の制限がない場合、Partition Key + Sort Keyで表現可能

|PK|SK|Attributes|Attributes|
|------|-----------|----|-----|
|USER#A|#PROFILE#AP|name|email|
|USER#A|ORDER#1|orderId1|status1|
|USER#A|ORDER#2|orderId2|status2|

* ORDERとPROFILEのAttributesが違う。DynamoDBはAttributeをKeyの内容によって自由に構成可能。

3. Secondary index + Query

TODO:

## Filtering

TODO:
