# gradle build error対策

いきなりIntellijのGradleビルドエラーになったので、ビルドエラー解決方法を調べてみた。

~~でもビルドエラーが解決できなかった~~

Gradleビルドができない場合、SpringBootのアノテーションが動かない場合に実行してみよう。

### Gradle Refresh

IntelliJ->Gradle Tab->Refresh

### Project Structure -> Problem

buileエラーが表示される

### File -> Cache　削除

IntelliJのCache削除

File->Invalidate Cache

### Re Import

https://jojoldu.tistory.com/364

* build.gradle右クリック->Import Gradle Project実行
* プロジェクトの設定ファイルを作成すると、再インポートされる
   * rm -rf ./.idea

