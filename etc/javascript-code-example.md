* 整数が1から連番である配列の中の合計
* ex [1, 2, 3] => 6, [1, 2, 3, 4, 5] => 15 

```javascript
const sum = (arrayLen * (arrayLen+1)) / 2;
```
<br>

* Valueが同じであるN個の配列新規作成

```javascript
Array(5).fill(0)
// [0,0,0,0,0]
```
<br>

* 合計値の+ - 計算

```javascript
sum += i;
// sum = sum + i;

sum -= i
// sum = sum - i;
```
<br>

* 配列操作

```javascript
const array = [1,2,3]

// 配列の最初に追加
array.unshift(4); // 4
console.log(array); // [4,1,2,3]

// 配列の最後を取り出す
array.pop(); // 3
console.log(array); // [4,1,2]
```



