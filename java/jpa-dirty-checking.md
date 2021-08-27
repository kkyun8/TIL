# Dirty Checkingとは？

https://jojoldu.tistory.com/415

* JPA（主にQueryDsl）でSelectしたEntityをちょっといじったら自動にUpdateされること


~~は？~~

DirtyCheckingって単語のことはただ「状態に変化が起きた」ぐらいなことで理解すればOK

## なぜこんなことが起こるのか？


* JPAではトランザクションが終わった時点で変化があった全てのEntity Objectをデータベースに自動に反映する


~~優しすぎる~~


## 自動反映を回避しよう

TODO
