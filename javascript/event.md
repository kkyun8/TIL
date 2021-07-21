# event Bubbling, Capture, Delegation & stopPropagation　& closest

https://joshua1988.github.io/web-development/javascript/event-propagation-delegation/#%EC%9D%B4%EB%B2%A4%ED%8A%B8-%EC%BA%A1%EC%B3%90---event-capture

基本の中で基本、VanillaJSのことを、まとめよう

## event Bubbling

* 画面でEventが発生し、発生した要素の「上位要素」にEventが電波されること。

## event Capture

* Bubblingと反対
* 画面でEventが発生し、発生した要素の「最上位要素」がEventが発生した「要素」を探すこと。

addEventListener() に { capture:true } オプションをつけたら動作する。

## event Delegation

https://ui.toast.com/weekly-pick/ko_20160826

* 上位要素が下位要素のEventを管理・検知すること。

## event.stopPropagation()

* 電波を止めること

## event.target.closest(要素値)

* Eventターゲットで一番近い要素を探す
