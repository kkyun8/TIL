<!--
Vue.js
면접관을 Vue.js 비사용자라고 가정하고 Vue.js에 설명하고 장단점을 말해달라
Vue.js의 Life-cycle에 대해 아는대로 말해달라
Vue.js 에서 DOM은 어느 시점에 생성되나
Computed와 Methods의 차이점은 무엇인가
가상돔(Virtual DOM) 개념은 무엇이며, DOM과의 차이점 가상돔의 개념이 사용되게된 배경은 무엇인가
최근의 프레임워크를 사용할때 외부 라이브러리와의 결합시에 더 나은 코드 작성법을 고민해본적이 있는가
DOM을 직접 조작하는 D3.js 같은 라이브러리와의 결합시에 예상되는 문제점이 있는가
TODO:
-->


## Vuejs V2 関連質問まとめ

### Vuejsを全く知らない人に、Vuejsについて、Vuejsの良いところと悪いところについて説明してください。

* Vuejs簡単説明
  * VuejsはMVVM(Model-View-ViewModel)パターンのJsフレームワークです。
  * Vuejsの特徴はHTML&CSS&JSを１つのコンポーネント（Web画面を部品みたいに作って再使用できるようにすること）ファイルに記入できるので、初心者でもわかりやすいし、プロジェクト管理しやすいフレームワークです。
  * VuejsみたいなJSフレームワークは他にReact、Angularがあります。

* 良いところ：
  * 他のJSフレームワークに比べてわかりやすい・軽い
    * Webページを構成するHTML、CSS、JSがはっきり別れてる構成なので、初心者も学びやすい
* 悪いところ：
  * Typescriptと連携が難しい
    * この問題を解決するため、Vue3でバージョンアップした
  * コンポーネントごとにCSSをかけるか、全体的な構成をみるとコンポーネント内にCSSを書くのはあんまり良くない

### VuejsのLife-cycleについて説明してください。

https://medium.com/witinweb/vue-js-%EB%9D%BC%EC%9D%B4%ED%94%84%EC%82%AC%EC%9D%B4%ED%81%B4-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0-7780cdd97dd4

＊V2の場合

* Creation 初期化、コンポーネントがDOMに追加される前
  * beforeCreate
    * data、 events(vm.$on, vm.$once, vm.$off, vm.$emit)がセッティングされてない時点
  * created
    * data、 events(vm.$on, vm.$once, vm.$off, vm.$emit)がセッティングされてる
    * template、仮想DOMはまだMount,Renderingされてない時点
* Mounting DOM設定
  * beforeMount
    *　初回レンダリングが発生する前の直前に実行される 
  * mounted
    * コンポーネント、テンプレート、レンダリングされたDOMに接近できる
    * ※Mountedだけは、親子実行順番が特別。ChildのMountedが終わったら、ParentのMountedが実行される
* Updating　DIFF・再レンダリング
  * beforeUpdate
    * コンポーネントのデーターが変換され、update cycleがはじまる場合呼びだされる
  * updated
    * 再レンダリングが終わった後に実行される
* Destruction　解体段階
  * beforeDestroy
    * Vue Instanceが解体される直前に呼び出される
    * EventListener、reactive subscriptionを削除する作業におすすめ 
  * destroyed
    * Vue Instanceが解体された直後に呼び出される

### VuejsでDOMはどの時点で生成されるのか

* beforeMountとmountedの間

### Virtual DOMについて説明してください。DOMと違うところと、なぜVirtual DOMを使うのか説明してください。

* DOM（Document Object Model）は基本的にHTMLマークアップとHTML要素のためのオブジェクトで構成されてます。このオブジェクトはTree構造になってますが、ブラウザはこの構造をWebページをローディングする際に作ります。
* Webアプリケーションの規模が大きくなると、DOMを直接制作することは、時間がかかるし、非効率的になるので VirtualDOMを使います。
* VirtualDOMでWebアプリケーションを構成するとDOM（Html、CSS）を仮想（Javascript）で作成することができ、Webアプリケーションを効率的に管理できます。


* VirtualDOMの目的
  * DOMをよく変更するとパフォーマンスが悪くなるので、VirtualDOMで変更が必要なところだけ変更してパフォーマンスをよくする
  * 軽く、効果的にVirtualDOMとDOMの差異を計算するために利用する


### v-modelについて説明してください。

```
...
「双方向 (two-way) データバインディング」を作成するには、v-model ディレクティブを使用することができます。-vue.js公式サイト
...
```
Data変数とフォームの値を連動させることができる。

dataで変更されたらフォームにも変更されるし、逆でフォームで変更されたらdataも変更されるので「双方向」バインディング。


### Computed vs Methods vs Watchの違いについて説明してください。

* Methodsは「関数」。呼び出したら実行されるもの。 Templateに宣言されたら、レンダリングされた場合実行される
* Computedは「算出プロパティ」。対象になるGetter、Setterができる、既存のデーターに対して処理をした結果を出す。
  * 依存するデーターが変更されたら、キャッシュされ、再算出する
* Watchは「監視プロパティ」。すでにセットされてるプロパティを監視する

### Vue(v2) + Typescriptの開発経験があれば説明してください。

参考になった記事
https://meetup-jp.toast.com/1843

Typeをしっかり管理する方がいいと思って、上記の記事のようにvue-property-decoratiorを積極的に活用して開発した。

上記のように実装したら、ソースが既存のVueとかなり変わるし、コード統一が難しいということがあるか、

それよりはTypeをしっかりすることが優先だと思ったので、上記の記事のように実装した。

<!--
＊V3
V3でComposition API 


### Virtual DOMについて説明してください。DOMと違うところと、なぜVirtual DOMを使うのか説明してください。

### フレームワークを使う場合、外部ライブラリとの結合で、よりいいコード作成方法を悩んだことがありますか？

### DOMを直接操作する

-->
