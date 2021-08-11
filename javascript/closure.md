~~もう一回まとめてみたぁ~~

## Closureとは？

Googleで検索した内容をまとめてみた

* クロージャ(closure)は内部関数が外部関数のコンテキストに接近することを示す。
* 関数内で関数を定義し（内部関数）、それを使ったら（内部関数を外部で使う）クロージャという。

必ず勉強して置かないといけないものだ。よく頭に入ってこないのは実際にJavascriptで使ったことが少ないのが（全くないかも）原因だと思う。

クロージャを理解するためには「実行コンテキスト」と「レキシカル環境」について理解が必要。JSがどうやって動いて、どこでなくなる

TODO
* 実行コンテキスト
* レキシカル環境
* スコープ

TODO
* 要するに、関数の環境になるものがメモリで消滅したので呼び出したできない状態だが、クロージャは環境（コンテキスト）を全部覚える環境になる


### 動作例


https://yuddomack.tistory.com/entry/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%ED%81%B4%EB%A1%9C%EC%A0%80Closure


```javascript
function outer(){
  var name = 'yuddomack';
  function inner(){
    console.log(name);
  }
  return inner;
}

var innerFunc = outer();
innerFunc();
```javascript



1. outer関数のnameを参照
2. var innerFunc = outer();で [innerFunc]はouter>innerまで取得
3. 一般的に関数が終了したらメモリから削除されるので、nameの参照はメモリで削除されてるはず
4. でもinnerFunc>>innerでnameが可能、可能なのはクロージャが環境全てを覚えるようにしてるため

### クロージャのカプセル化

* クロージャを利用したらまるでPrivateみたいな形ができる

```javascript
function student(name, score){
  // var name = name, score = score;
  return {
    setScore: function(_score){
      score = _score;
    },
    getInfo: function(){
      return { name:name, score:score };
    }
  }
}

var lee = student("sunsin", 80);
var kim = student("yusin", 75);

lee.setScore(60);

console.log(lee.getInfo()); // { name: 'sunsin', score: 60 }
console.log(kim.getInfo()); // { name: 'yusin', score: 75 }
```

こういうふうにやると同一なStudent関数になってるけど、それぞれ独立でクロージャが作成される

Closureを使ったらまるでシングルトーン見ないな関数の作成ができる

### メモリ効率には良くない


クロージャはスコープの中の変数がスコープ終了と同時に回収ができない。スコープの外側でいつでもその変数を呼び出す可能性があるため、Javascriptはその変数を「メモリに連続的に保存」する。

なので、メモリに効率できな作業方法ではない。「回収できない特性」があるため、絶対に必要な場合に使うのがおすすめ。


### なぜクロージャを使うのか？？

