## 객체와 자료구조
### 추상화: 구현 감추기
### 자료와 객체의 차이
```
// 절차적인 코드
data class Square(var topLeft: Point, var side: Double)
data class Rectangle(var topLeft: Point, var height: Double, var width: Double)
data class Circle(var center: Point, var radius: Double)
class Geometry {
    fun area(shape: Any): Double {
        return when(shape){
            as Square -> shape.side * shape.side
            as Rectangle -> shape.height * shape.width
            as Circle -> 3.14 * shape.radius * shape,radius
            else -> 0.0
        }
    }
}

// 객체지향적인 코드
class Square(var topLeft: Point, var side: Double): Shape {
    fun area: Double = side * side
}
class Rectangle(var topLeft: Point, var height: Double, var width: Double): Shape {
    fun area: Double = height * width
}
class Circle(var center: Point, var radius: Double): Shape {
    fun area: Double = 3.14 * radius * radius
}
```
- 특징
  - 자료: 새로운 자료 타입 추가 어려움, 새로운 함수 추가 쉬움
  - 객체: 새로운 자료 타입 추가 쉬움, 새로운 함수 추가 어려움

### 디미터 법칙
> 허용된 메서드가 반환한 객체의 메서드를 호출하면 안된다는 법칙
