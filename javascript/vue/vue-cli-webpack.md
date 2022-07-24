# vue-cliで簡単webpack設定

## vue-cliのvue.config.jsの「configureWebpack」でWebpack設定ができる

公式ガイド
https://cli.vuejs.org/guide/webpack.html#simple-configuration

#### 公式ガイドのプラグイン例

```
// vue.config.js
module.exports = {
  configureWebpack: {
    plugins: [
      new MyAwesomeWebpackPlugin()
    ]
  }
}
```

#### webpackのpluginを利用する例

```
// vue.config.js
//　 webpackを読み込む
const webpack = require('webpack');
module.exports = {
  configureWebpack: {
    plugins: [
      new webpack.ProgressPlugin()
    ]
  }
}
```


## vue-cliでビルド改善

### build後のJSファイルの大きさ確認できる「webpack-bundle-analyzer」

ビルドしたJSファイルのサイズをわかりやすく確認できる。

https://github.com/webpack-contrib/webpack-bundle-analyzer

![image](https://user-images.githubusercontent.com/46196432/180651967-635333c0-e375-41f7-807b-1a712089e1b3.png)

### vue-cliの場合は、--reportを使うと「webpack-bundle-analyzer」が実行される

https://cli.vuejs.org/guide/cli-service.html#vue-cli-service-build

```
 --report       generate report.html to help analyze bundle content
```

```
// 下記のコマンドを実行するとdist/report.htmlが作成され、「webpack-bundle-analyzer」の実行結果が確認できる
yarn build --report
```

### pluginを使ってmoment.jsのビルド改善

momentjsはビルドサイズが大きいライブラリーで良く知られているものだ。

サイズが大きい原因は、世界時間を表示するための各地域の情報が入ってるlocaleのことで、不要な地域の時間を除外するだけでビルドサイズが小さくなる。

https://qiita.com/jimbo/items/95da1c223ad25a33ed16

```
// vue.config.js
//　 webpackを読み込む
const webpack = require('webpack');
module.exports = {
  configureWebpack: {
    plugins: [new webpack.ContextReplacementPlugin(/moment[/\\]locale$/, /ja/)],
  }
}
```

#### ビルドサイズが大きいライブラリー例

* vuetify
* moment
* lodash

### production環境でSourceMapを非活性

```
module.exports = {
  productionSourceMap: false,
};
```

## vueのビルド改善について参考したサイト

* https://ui.toast.com/weekly-pick/ko_20190603
* https://ui.toast.com/weekly-pick/ko_20200128
