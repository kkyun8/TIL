# gradle build error対策

いきなりIntellijのGradleビルドエラーになったので、ビルドエラー解決方法を調べてみた。

~~でもビルドエラーが解決できなかった~~

Gradleビルドができない場合、SpringBootのアノテーションが動かない場合に実行してみよう。

### javaファイル認識ができない場合

* SourceRoot再設定設定
    * https://pleiades.io/help/idea/content-roots.html
* File >> Project Structure >> Project Setting/Modules がちゃんと設定されてるか確認

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

