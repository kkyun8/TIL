## ReactとTypescriptを使う時に考えること

### 関数コンポーネントで実装するなら、React.FC<P>を避けること(アロー関数式を避ける)
https://darrengwon.tistory.com/768
blog.variant.no/a-better-way-to-type-react-components-9a6460a1d4b7


  
* 関数コンポーネントを使った方がいいか調べてるところ、いいブログがあったのでまとめてみた
  * 変数に直接Propを使うと、構成要素を明確に入力ことができる・誤りをなくせる
  * 特定のフレームワークに合わせることではなく、Typescriptのタイピングのポリシーに合わせた方がいいこと
  * React公式でもfunctionを使うことをお勧めしてる


例
  
  
```javascript
//アロー
import React from "react";

interface IProps {
  name: string;
}

const Greeting: React.FC<IProps> = ({ name }) => {
  return <div>hello {name}</div>;
};

export default Greeting;  
```
  
```javascript
//普通
import React from "react";

interface IProps {
  name: string;
  job?: string;
}

function Greeting({ name, job }: IProps) {
  return (
    <div>
      hello {name} {job}
    </div>
  );
}

export default Greeting;
```

  
  
  
  
  
