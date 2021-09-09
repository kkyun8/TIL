# QueryDSLでFetchJoinとPaginationを一緒に使ったら？

ネットで調べてみたら、FetchJoin＋Paginationについていい説明（韓国語）あったので、まとめてみた

https://javabom.tistory.com/104

現場で起こったこともあった。

## 結論から言うと、FetchJoinとPaginationを一緒に使うなら警告メッセージが出る
 
```
HHH000104: firstResult/maxResults specified with collection fetch; applying in memory!
```

Query結果を全部メモリに積んでから、Pagnination作業をアプリケションでやるから危ないってメッセージ~~???~~

<br>

## 警告が出るけとPaginationは動いてるのか？


以下のようにOneToMany（1:N）を前提でメインになるところ（Article）にLimitをセットしたのになぜエラーが出たのか？


```
 public List<Article> findArticleByIdLimit5Fetch(Long id) {
        return queryFactory.selectFrom(article)
                .innerJoin(article.comments, comment).fetchJoin()
                .where(article.id.eq(id))
                .limit(5)
                .fetch();
    }
```


以下のSQLが出ると思って上記のQueryDSLを作成したが、


```
SELECT *
FROM article
INNER JOIN comment ON article.id = comment.article_id
WHERE article.id = ?
LIMIT 5
```


実際はLimitがないものがSQLになる


```
Hibernate: 
    select
        article0_.id as id1_0_0_,
        comments1_.id as id1_1_1_,
        article0_.contents as contents2_0_0_,
        comments1_.article_id as article_3_1_1_,
        comments1_.contents as contents2_1_1_,
        comments1_.article_id as article_3_1_0__,
        comments1_.id as id1_1_0__ 
    from
        article article0_ 
    inner join
        comment comments1_ 
            on article0_.id=comments1_.article_id
```


<b>こうなった理由は、簡単に言ったら、Fetch Joinを使うなら、LimitをNullに設定することが入ってるからだ</b>


<br>


## メモリー警告が出るのはFetchのことで

Fetchして持ってくる（Comment）が多くて、メモリに積んでしまう量が増えるので、メモリに負担がかかるから警告メッセージが出る。


<br>


## 簡単な解決方法は、別々に使うか、ManyToOneでやるか、FetchJoinとPaginationはやめよう


ManyToOneを条件にするとMemory警告が発生しない


```
public List<Comment> findCommentByArticleIdLimit5(Long id) {
        return queryFactory.selectFrom(comment)
                .innerJoin(comment.article, article).fetchJoin()
                .where(article.id.eq(id))
                .limit(5)
                .fetch();
    }
```

