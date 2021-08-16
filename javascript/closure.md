~~もう一回まとめてみたぁ~~

## Closureとは？

Googleで検索した内容をまとめてみた

* クロージャ(closure)は内部関数が外部関数のコンテキストに接近することを示す。
* 関数内で関数を定義し（内部関数）、それを使ったら（内部関数を外部で使う）クロージャという。
* シンプルには<u> 「関数の外側で宣言した変数を関数の内部で使う場合　、クロージャが生成されること」<u>を覚えて。


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

* 情報を隠し、キャップセル化できるから

1. ボタンをクリックする際に、カウントされるロジックを作る
1. ボタンをクリック→Onclick Eventが発生して、関数「updateClickCount()」が呼び出すようにコード作成、<button onclick="updateClickCount()">click me</button>
1. ここでupdateClickCount関数を作成するいくつかの方法がある

TODO
  
<!--
closure를 사용하는 한 가지 시나리오를 보여주고 글을 마무리 하겠습니다.
사용자가 버튼을 클릭할 때, count를 세는 기능을 만든다고 가정하겠습니다.
버튼을 클릭할 때, onclick 이벤트가 발생 해 updateClickCount 함수가 호출 되도록 코드를 만들었습니다.
<button onclick="updateClickCount()">click me</button>
여기서 updateClickCount 함수를 만드는 여러 방법들이 있습니다.
global 변수를 선언하고 함수에서 counter를 증가시킨다.
var counter = 0;

function updateClickCount() {
    ++counter;
}
이 방법의 문제는 updateClickCount 함수의 호출 없이 페이지에 있는 다른 스크립트에 의해 counter 값이 0으로 초기화 될 수 있습니다.
2. 변수를 함수안에 넣는다면.
function updateClickCount() {
    var counter = 0;
    ++counter;
}
함수 호출 할 때마다 couter 값이 0 이 되버리는 문제가 있네요 ^^;
3. 중첩 함수를 이용해볼까?
function countWrapper() {
    var counter = 0;
    function updateClickCount() {
    ++counter;
    }
    updateClickCount();    
    return counter; 
}
위 코드에서 updateClickCount는 중첩 된 함수 countWrapper Scope에 선언 된 변수 counter에 대해 접근할 수 있습니다. 이 방법은 counter에 대한 문제를 해결하지만, 외부에서 updateClickCount함수를 직접 호출하면 counter=0을 단 한번 호출하도록 방법을 찾아야 합니다.
4. Closure가 살길이네여 ㅇ.ㅇ
var updateClickCount=(function(){
    var counter=0;

    return function(){
     ++counter;
    }
})(); // 즉시 호출
위에서 updateClickCount는 선언과 동시에 딱 한번 실행됩니다. 내부에서 counter 값을 0으로 set하고 익명의 함수를 리턴합니다. 리턴되는 익명의 함수는 Closure를 통해 counter의 값에 접근할 수 있습니다. Closure를 통해 리턴되는 함수가 private 변수 counter를 가지도록 해주는 셈이죠. 변수 counter는 익명 함수의 Scope에서 안전하게 보호되고 함수를 통해서만 값의 변경을 허용합니다.
-->
