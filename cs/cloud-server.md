# クラウド Cloudとは

<!-- TODO -->

## クラウドサービス

## on-premise オンプレ


~~Googleから~~

```
オンプレミスは、サーバーやソフトウェアなどの情報システムを、

使用者が管理している施設の構内に機器を設置して運用することを指す。「オンプレ」と略されることもあるほか、「自社運用」とも呼ばれる。
```

クラウドではなく、自社でサーバーなどを構成すること。


https://www.redhat.com/ko/topics/cloud-computing/iaas-vs-paas-vs-saas#:~:text=%ED%81%B4%EB%9D%BC%EC%9A%B0%EB%93%9C%20%EC%BB%B4%ED%93%A8%ED%8C%85%20%EC%84%9C%EB%B9%84%EC%8A%A4%EB%8A%94%20%EC%84%9C%EB%B9%84%EC%8A%A4,%EA%B0%80%EC%A7%80%20%EA%B8%B0%EB%B3%B8%20%EC%9C%A0%ED%98%95%EC%97%90%20%ED%95%B4%EB%8B%B9

## SasS Software as a Service

Ex:Google Workspace(旧 G Suite) 、Salesforce、Gmail

* 全てのアプリケーションは提供会社が管理するし、Webブラウザを使って提供
* 提供会社がアップデート、バグ修正などを行う
* Clientは別のSoftwareをインストールする必要がない
 
## PasS Platform as a Service

Ex: AWS Elastic Beanstalk, Heroku

* PasSはオンプレミス・インフラ管理が「もっと発展した形」
* PasSは提供会社が【自社インフラでハードウェア・ソフトウェア】をホスティングしてクライアントに「ソリューション・インターネットを通じた」サービスで提供する。
* クライアントはアプリケーションコードを作成・ビルド・管理するか、【ソフトウェアアップデート・ハードウェア維持保守】みたいなめんどい作業がなくなる。
  
## IaaS Infrastructure as a Service

Ex:AWS, Microsoft Azure, Google Cloud　「Public Cloud」

* IaaSはオンプレミス・インフラ管理が「一段階発展した形」
* 従量制クラウドサービス
* クライアントは【OS、データー、アプリ、ミドルウェア】を担当し、提供会社はクライアントが必要とする【ネットワーク、サーバー、仮想化・ストレージ】みたいなインフラサービスをインターネットを通じてクラウドで提供する。

## IaaS > PasS > SasS

機能としては　IaaS > PasS > SasS
