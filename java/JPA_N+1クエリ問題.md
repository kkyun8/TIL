# JPA_N+1クエリ問題

ネットでいい記事があったのでまとめてみた。韓国語と日本語両方ある。さすがNHN
https://meetup.toast.com/posts/87
https://meetup-jp.toast.com/874

## JPA N+1

簡単にまとめると、Entityで@OneToMany、@ManyToOneを設定して、FindAllをすると、

Left Joinではなく、ManyToOneしたEntityに複数のSQL（単純のWhere ID＝）が発生して、

無駄なSELECT SQLが大量に発生することだ。

## 解決はQueryDSL

記事を見るとQueryDSLを使うことをおすすめするし、韓国ではQueryDSLがよく使われてるらしい。。

## FetchType.LAZY、EAGER

即時ローデイング、遅延ローディングの違い。
TODO
