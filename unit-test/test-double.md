#  ユニットテストの基本、テストダブルにについて考えてみよう

* https://ja.wikipedia.org/wiki/%E3%83%86%E3%82%B9%E3%83%88%E3%83%80%E3%83%96%E3%83%AB
* https://cobbybb.tistory.com/16#Test%--Double%---Mockito-
* https://qiita.com/kaleidot725/items/075934e8e6be902a7fe1

現場でユニットテストコードを書いてるか、深い理解がまだできてないので、まとめてみた。

## ユニットテスト、その範囲は？

* 最近JUnitでユニットテストコードを書く際に、どこをMockにして、どこをSpyにするかなど、全体的な構成がすぐ思い出さないので、ユニットテストコードを書くのに時間がかかってる。
* テストコードのファイルのモック化設定（MockかInjectMockか、、など）について整理してみる。
* これはJUnitとJestなど、ユニットテストフレームワークの種類と関係がない、ユニットテストを書くなら必要な知識。

### 1.対象になるクラス（Service）は自分しか知らない

* 例えば JUnitでServiceクラスを対象でユニットテストコードを書くなら、そのServiceの中にあるRepositoryの確認は（Repositoryが正常に動くのか）いらない。
* Repositoryのユニットテストは別で行うので、RepositoryのFindAllみたいなけっけをServiceをテストする際にはMockにすればいいこと。
* そのRepositoryの例外処理などもMockにして、ちゃんと例外ハンドリングできてるのか「Service」の範囲で確認すればいい。

### 2.Mock Spy Stub..これの役割、違いは？
 TODO
