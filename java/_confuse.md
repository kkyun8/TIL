# JAVAで混乱しやすいまとめ

## Overloading VS Overriding

https://gmlwjd9405.github.io/2018/08/09/java-overloading-vs-overriding.html

### Overloading

Method名が同じか、パラメーターの数か、パラメーター型が異なる場合

```java
public double computeArea(Circle c) { ... }
public double computeArea(Circle c1, Circle c2) { ... }
public double computeArea(Square c) { ... }
```

### Overriding

親のMethodを再定義して使うこと。

```java
public abstract class Shape {
  public void printMe() { System.out.println("Shape"); }
  public abstract double computeArea();
}
public class Circle extends Shape {
  private double rad = 5;
  @Override // @Override(annotation) がわかりやすいので使おう
  public void printMe() { System.out.println("Circle"); }
  public double computeArea() { return rad * rad * 3.15; }
}
public class Ambiguous extends Shape {
  private double area = 10;
  public double computeArea() { return area; }
}
```
