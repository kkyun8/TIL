* 基本js（ブラウザー内）のthisは<b>windowオブジェクト</b>
* <b>関数functionの場合、ThisはグローバルオブジェクトGlobal objectを対象にする。</b>
  * これはobjectの中に, functionの中に setTimeoutみたいなcallBackにも同じ
* しかし、<b>objectのvalueで宣言された関数の場合、thisは親になるobjectを対象にする</b>


```javascript
var value = 1;

var obj = {
  value: 100,
  foo: function() {
    var that = this;  // Workaround : this === obj

    console.log("foo's this: ",  this);  // obj
    console.log("foo's this.value: ",  this.value); // 100
    function bar() {
      console.log("bar's this: ",  this); // window
      console.log("bar's this.value: ", this.value); // 1

      console.log("bar's that: ",  that); // obj
      console.log("bar's that.value: ", that.value); // 100
    }
    bar();
  }
};

obj.foo();
```

* thisをバインディングして関数を実行する「apply call bind」メソッドを使う + arguments
  * arguments オブジェクトはすべての（アローではない）関数内で利用可能なローカル変数。　
  * arrayににってるかarrayではない。関数のパラメーターを参照できる。
    * func.call(context, ...args)
    * func.apply(context, args)


```javascript
var value = 1;

var obj = {
  value: 100,
  foo: function() {
    console.log("foo's this: ",  this);  // obj
    console.log("foo's this.value: ",  this.value); // 100
    function bar(a, b) {
      console.log("bar's this: ",  this); // obj
      console.log("bar's this.value: ", this.value); // 100
      console.log("bar's arguments: ", arguments);
    }
    // objをthisにしてbar実行
    bar.apply(obj, [1, 2]);
    bar.call(obj, 1, 2);
    bar.bind(obj)(1, 2);
  }
};

obj.foo();
```
