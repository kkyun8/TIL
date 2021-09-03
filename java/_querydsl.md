# SpringBootQuery条件でQueryDslを使ってみよう

https://querydsl.com/static/querydsl/4.0.1/reference/ko-KR/html_single/#creating_queries

https://joont92.github.io/jpa/QueryDSL/

https://ict-nroo.tistory.com/117

https://velog.io/@kangsan/%EC%82%AC%EB%82%B4-%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8-Dynamic-Query-%EC%A0%81%EC%9A%A9%EA%B8%B0

## 概要

JPAの条件を動的に使いたいと思って、「Specification」と「QueryDsl」を比較してみた

結局、「QueryDsl」を使ってみようと思った

## なぜ「QueryDsl」？

### なぜ「QueryDsl」がいいのか、ネットでまとめた文章があった（原本は韓国語）

* JpaSpecificationは結局JPAが提供するCriteriaで構成され、JPAのCriteriaは少しでも複雑になったら、実務で使うのが難しくなる。（コードが読みにくい）
* Queryが複雑になる可能性（複数のJoinなど）があるなら絶対「QueryDsl」がいい
* そして個人的に、JPAのN:1問題の解決がうまくいかなかったから、EntityのOneToManyではなく、QueryのLeftJoinで問題を解決しようと思ったので、「QueryDsl」を選択。https://meetup-jp.toast.com/874

### 仕事でQueryDslを使った人のコメント

* データベースデーブルが変更されても柔軟に対処できる
* データベースが変更されても影響が少ない
* エラー確認が簡単だし、Queryバグはほとんど発生しない


## でも実際の現場では使えなかった

下記の理由で使えなかった。

* QueryDslは「検索文字 like カラム」みたいなカスタムSQLはかけることができない。DB設定はSQLなどを工夫したら「検索文字 like カラム」の問題は解決できそうだが、、時間がなかった。
* なぜかBuildがうまくいかなくて、QueryDslのEntityが自動作成できない時があった。不安定。。
