

## 이름
### 의도가 분명히 드러나는 이름
```
var d: Int                    (x)
var daysSinceCreation: Int    (O)
```

### 그릇된 정보
> 의미 있는 단어를 다른 의미로 사용(예: accountList)

### 의미 있게 구분
```
// 연속된 숫자
n1, n2, n3...    (X)

// 불용어
var name_string = "X"
var name = "O"
```

### 기타
```
// 헝가리식 표기법
var value_of_number    (X)

// 접두어
var m_context          (X)
```

---  
### 클래스 이름
```
// 명사구 (O)
Cuustomer, WikiPage...
```

### 메소드 이름
```
// 동사구 (O)
postPayment, deletePage...
get, set, is...
```

### 기타
- 기발한 이름 (X)
- 한 개념에 한 단어 (X)
- 말장난 (X)
- 해법 영역
- 문제 영역
- 의미 있는 맥락
- 불필요한 맥락 제거



## 함수
### 최대한 작고 한 가지 기능만 수행
- 코드가 길면 길수록 읽기 어렵다.
- 하지만 함수가 한가지 기능만 수행한다면
- 코드가 명백해지고 읽기도 쉬워져서 유지보수가 쉬워진다.

### switch문(코틀린에선 when문)
> 완전히 피할수는 없어도 피하려는 코딩 스타일을 유지하자
```
fun multi(n: Int){
    when(n){
        1 -> {}
        2 -> {}
        else -> {}
    }
}
```

### 서술적 이름
[Clean Code 이름]()
```
testableHtml -> SetupTeardownIncluder
```
---
### 인수
- ##### 플래그 인수
> 함수에 논리값을 전달하는 관례로 쓰는 것을 피하는 것이 좋다.
- ##### 이항 함수
> 단항 함수보단 어렵지만 Point(x, y)와 같은 적절한 예시도 있다.
- ##### 삼항 함수
> 이항 함수보단 어려우므로 특수한 상황이 아닐시 쓰는 것을 권장하진 않는다.
- ##### 출력 인수
> 받아오는 인수를 변형시켜 반환하는 함수  
가능하면 출력인수를 사용하진 말고 입력인수를 변환시키는 함수를 사용하길 바란다.
### 부수효과
```
// 아래는 굉장히 과장했지만 if문을 두번 사용하고 다른 기능을 사용하듯이 함수가 한가지를 사용한다는 원칙을 위배했다.

fun printOnScreen(str: String?){
    if(str != null){
        println("입력값이 널이 아닙니다.")
        if(str.size != 0){
            println(str)
            outStrim(str)
        }
        else {
            println("입력값이 없습니다.")
        }
    }
}
```

### 기타
- 들여쓰기
- 내려가기 규칙
- 함수의 추상화 수준
- 명령과 조회 분리
- 오류보단 예외 사용
- 반복하지 않기


## 주석
> 1. 왠만해선 안쓰는 것이 좋다.  
> 2. 나쁜 코드를 보완하진 못한다.  
> 3. 코드로 의도를 표현하자

### 좋은주석
- 법적인 주석
- 정보를 제공하는 주석
- 의도를 설명하는 주석
- 의미를 밝히는 주석
- 결과를 경고하는 주석
- TODO 주석
- 중요성을 강조하는 주석
- 공개 API에서 Javadocs

### 나쁜주석
- 주절거리는 주석
- 같은 이야기를 중복하는 주석
- 오해할 여지가 있는 주석
- 의무적으로 다는 주석
- 이력을 기록하는 주석
- 있으나 마나 한 주석
- 무서운 잡음
- 함수나 변수로 표현할 수 있다면 주석을 달지 마라
- 위치를 표시하는 주석
- 닫는 괄호에 다는 주석
- 공로를 돌리거나 저자를 표시하는 주석
- 주석으로 처리한 코드
- HTML 주석
- 전역 정보
- 너무 많은 정보
- 모호한 관계
- 함수 헤더
- 비공개 코드에서 Javadocs


## 형식
> 코드형식은 너무너무 중요한 의사소통의 일환이다.
### 적당한 행 길이 유지
> 줄 수가 적은 코드들로도 대규모 시스템을 구축할 수 있으니 거대한 파일을 만들지는 말자
### 세로 밀집도
> 서로 밀접한 코드 행은 가까이 붙여 놓여야 한다.
### 수직거리
- 변수 선언: 사용 위치에서 최대한 가까이 선언
- 인스턴스 변수: 클래스 맨 처음에 선언
- 종속 함수: 호출한 함수와 호출받은 함수는 가까이 배치한다.
- 개념적 유사성: 개념적인 친화도가 높은 코드는 가까이 두는 것이 좋다.
### 가로 공백과 밀집도
- 연산자를 강조하기 위해 앞뒤로 공백을 줄 것
- 함수와 괄호 사이에는 공백를 넣지 않는다.
- 인수들은 공백으로 구분해준다 

### 기타
- 개념은 빈행으로 분리
- 들여쓰기


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