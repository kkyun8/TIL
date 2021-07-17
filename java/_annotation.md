# Spring Bootでよく使うアノテーション比較・整理

なんとなくわかっていたものを整理しよう

## @NoArgsConstructor VS @AllArgsConstructor VS @RequiredArgsConstructor 

https://ksshlee.github.io/spring/java/lombok/

* @NoArgsConstructor パラメーターがない基本コンストラクター
  * AccessLevelで接近者の指定ができる。
  * (access = AccessLevel.PROTECTED)で、オブジェクト生成する際に安全性を高めよう。
  * 基本設定である「public(default)」にしたら安全性が悪い。
* @AllArgsConstructor 全てのフィルドをパラメーターにするコンストラクター
* @RequiredArgsConstructor final、@NonNullであるフィルドをパラメーターにするコンストラクター
  * 使わない方がいい  


### おすすめする形（ビルダを利用）

```java
public static class User{
  private String pwd;
  private String id;

  @Builder
  public User(String pwd, String id){
    this.pwd = pwd;
    this.id = id;
  }
}

User user = User.builder().pwd("userPwd").id("userId").build();
```

## @Autowired VS @Resource VS @Inject

* よく使われてるAutowiredについて読んでおくこと~~多すぎ~~
   * https://yaboong.github.io/spring/2019/08/29/why-field-injection-is-bad/
   * https://www.mimul.com/blog/di-constructor-injection/
   * https://zorba91.tistory.com/238
   * https://qiita.com/KevinFQ/items/20a6d53a5f93e28ab9ef
   * https://withseungryu.tistory.com/65

* @Resource　：　javax.annotation
* @Inject　：　javax.inject
* @Autowired　：　org.springframework.bean.factory

1. @AutowiredはSpringフレームワークでつくあったものなので他のフレームワークに互換性が悪い。
2. 名前で検索するなら@Resource、Typeで検索するなら@Autowired、@Inject


## @Controller VS @RestController



### HTTP Response Body違い（Viewを使うか使わないか）

* 既存の MVC→ @Controllerは View を使うか
* @RestControllerは ObjectをリターンをJSON/XML タイプにする

@Controller　＋　@ResponseBody　にする方法もあるか、RESTなら＠RestControllerを使おう。


### 実行の流れ

* @Controller
  * Client -> Request -> Dispatcher Servlet -> Handler Mapping -> Controller -> View -> Dispatcher Servlet -> Response -> Client 

* @ResponseBody
  * Client -> Request -> Dispatcher Servlet -> Handler Mapping -> Controller (ResponseBody)-> Response -> Client 

* @RestController
  * Client -> HTTP Request -> Dispatcher Servlet -> Handler Mapping -> RestController (自動ResponseBody追加)-> HTTP Response -> 
