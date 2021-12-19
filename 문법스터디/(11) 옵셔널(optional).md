## 1. 옵셔널(optional)

- 옵셔널은 값이 '있을 수도, 없을 수도 있음'을 의미한다.
- 옵셔널은 nil 가능성을 문서화 하지 않아도 코드만으로 충분히 표현이 가능하다.
  > 문서/주석 작성 시간을 절약
- 전달받은 값이 옵셔널이 아니라면 nil 체크를 하지 않더라도 안심하고 사용할 수 있다.
  > 효율적인 코딩  
  > 예외 상황을 최소화하는 안전한 코딩


```swift
// Int 옵셔널 타입 명시
func someFunction(someOptionalParam: Int?) {
    // ..
}
// 파라미터에 값을 전달해줄 때 nil을 보낼 수 있다.
someFunction(someOptionalParam: nil)

// 옵셔널이 아닌 Int 타입을 명시
func someFunction(someParam: Int) {
    // ..
}
// 옵셔널이 아닌 타입에는 nil을 보낼 수 없다.
someFunction(someParam: nil) // 오류 발생

```

- 옵셔널 사용

```swift
// Int 값이 들어있을 수도 있고 없을 수도 있다라는 것을 의미
var optionalValue: Int? = 100 

switch optionalValue {
case .none :
    print("This Optional variable is nli")
case .some(let value) :
    print("Value is \(value)")
}

```
```swift
// nil 할당 가능
optionalValue = nil

// 기존 변수처럼 사용 불가 - 옵셔널과 일반 값은 다른 타입이므로 연산불가
optionalValue = optionalValue + 1 // 오류 발생

```

------------------

## 2.옵셔널의 기본 문법

```swift
// 옵셔널의 기본 문법
let optionalValue: Optional<Int> = nil

// 아래와 같이 작성할 수도 있다.
let optionalValue: Int? = nil

```

-------------------

## 3. 암시적 추출 옵셔널 (Implicitly Unwrapped Optional)

- 느낌표(!)를 사용한다.


```swift
var optionalValue: Int! = 100

// 옵셔널 타입 자체는 열거형이므로 switch-case구문으로 구분해줄 수 있다.
switch optionalValue {
case .none:
    print("This Optional variable is nil")
case .some(let value) :
    print("Value is \(value)")
}

```

- 옵셔널 사용

```swift
// 기존 변수처럼 사용 가능
optionalValue = optionalValue + 1

// nil 할당 가능
optionalValue = nil

// 잘못된 접근으로 인한 런타임 오류 발생 : 위에서 nil을 할당했는데 optionalValue에 접근하기 때문
optionalValue = optionalValue = 1

```


-------------------
출처 : [Swift 문법강좌](https://www.youtube.com/playlist?list=PLz8NH7YHUj_ZmlgcSETF51Z9GSSU6Uioy)

