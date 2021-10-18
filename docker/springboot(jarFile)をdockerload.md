# springbootビルドしたjarファイルをdocker loadでデプロイしたら適用されるもの

saveしたイメージでデプロイしたい場合、

docker-compose up した後、docker loadすると適用できる（application.propertiesはサーバー上のものに適用）


* jarを適応したいならimage作成（save load）
* プロパティ適応はコンテナ作成

