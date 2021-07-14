# Spring Bootでよく使うアノテーション比較・整理

なんとなくわかっていたものを整理しよう

## @Autowired VS @Resource VS @Inject

* 実はAutowiredを使うのはお勧めしてない（InteliJで警告）か、現場では　Repository DIによく使ってる

<!--
@Autowired VS @Resource VS @Inject
앞서 확인했던 내용을 하나의 표로 정리하면 다음과 같습니다.

 @Inject과 @Autowired는 서로 대체가 가능한데 무슨 차이점이 있을까요??

먼저 @Inject은 Java에서 지원하고 @Autowired는 SpringFramwork에서 지원을 합니다.

두 애너테이션의  FQCN (fully Qualified Class Name)을 보면 바로 아실 겁니다.

@Inject : javax.inject.Inject 

@Autowired : org.springframework.beans.factory.annotation.Autowired

그래서 @Inject은 Spring에 종속적이지 않은 애너테이션이고, @Autowired는 Spring에서만 사용 가능합니다.

 

추가적으로 @Inject은 nullable 하게 만들 수가 없습니다. 무조건 빈을 주입받아야 하고 해당하는 빈이 없다면 에러가 발생합니다. (Spring 4.xxx , Java 8 이상 일 경우 Optional을 사용해서 할 순 있지만 애너테이션 자체에서 사용 가능한 속성은 없습니다.)

그러나 @Autowired은 @Autowired (required = false)와 같이 선언하면 참조 변수에 빈을 주입하지 못해도 에러가 발생하지 않고 null로 처리됩니다. 


 	@Autowired	@Resource	@Inject
의존성
주입순서	타입 -> 이름	이름 -> 타입	타입 -> 이름
빈 지정
방법	1. @Qualifier("빈 이름")
2. @Primary 사용	@Resource(name="빈 이름")	1. @Qualifier("빈 이름")
2. @Primary 사용
3. @Named(value="빈 이름")
Nullable	required=false 속성 사용	X	X
비고	SpringFramwork
안에서만 사용 가능	Java 9 이후로 삭제	특정 프레임워크에
종속적이지 않음
 

지금까지 각 애너테이션에 대해서 알아보았습니다.

개인적인 견해로는 @Resource는 사용하지 않는 것이 좋을 것 같습니다.

저는 @Autowired를 선호하는데 Spring으로 프로젝트를 진행하다가 중간에 프레임워크를 바꾸는 경우는 거의 없을 것 같고, Java언어로 웹 개발하는데 Spring을 안 쓰는 경우도 좀 드물 것 같네요.

그리고 사실 처음부터 @Autowired를 써왔어서 이게 제일 편하기도 합니다.~

@Autowired와 @Inject은 각자의 주관에 따라 사용을 하시면 될 것 같습니다.

-->


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
