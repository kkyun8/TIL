# JSのEventLoopとは？

JSのイベントループについてまとめてみよう

## EventLoopの前、Javascriptはの動きを知って置こう

* EventLoopアニメーション
* https://dev.to/lydiahallie/javascript-visualized-event-loop-3dif


## Javascript Engine

JS言語はJSエンジンというやつに通じて実行される。

このJavascript EngineはWebブラウザ内部か、NodeJSの中に構成されてる。エンジンは様々な種類があるか、一番有名なのはGoogleが開発したV8。

### Javascript Engineの内部構造

「Call Stack」と「Heap」に分かれてる。この二つのものが、「Engine」の「外部」のものと役割を部案たんしてJSコードを実行させる。

* CallStack　１つのCallStack。一回に一つの作業のみ実行できるので、一つの関数が実行されたら、他の関数の実行が終わるまでには他のTaskの実行ができない。
  * 非同期関数の場合、すぐ実行するではなく「WebAPI」に送る。
* Heapはメモリーを担当する。自動にメモリ管理をしてくれる
  * 自動にメモリを削除してくれることを「garbage collection」という。

## WebAPI

CallStackから受けた非同期処理関数（Callback）は、CallStackにいかず、すぐJSエンジンの外側で「Task Queue」へ移動する

## Task Queue（EventQueue）

WebAPIからうけだCallback関数が待機しているところ

## EventLoop

```
event loop のコンセプトは非常にシンプルです。無限ループで JavaScript エンジンはタスクを待機し、それらを実行し、また次のタスクを待機します。
```

TaskQueueにある関数（Event）をJSエンジンに渡す。



