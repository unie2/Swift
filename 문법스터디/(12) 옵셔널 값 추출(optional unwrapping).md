## 1. 옵셔널 바인딩 (Optional Binding)

- 개요

```swift
func printName(_ name: String) {
    print(name)
}

var myName: String? = nil // 옵셔널 타입

printName(myName) // 전달되는 값의 타입이 다르기 때문에 컴파일 오류 발생

```

- if-let 방식을 통해서 옵셔널 바인딩을 수행할 수 있다.

#### if-let

```swift
func printName(_ name: String) {
    print(name)
}

var myName: String? = nil // 옵셔널 타입

if let name: String = myName { // 상수 name은 if-let 구문 안에서만 사용이 가능하다
    printName(name)
} else {
    print("myName == nil")
}

// name 상수는 if-let 구문 내에서만 사용가능하다
// printName(name) // 상수 사용범위를 벗어났기 때문에 컴파일 오류 발생

```
![결과](https://user-images.githubusercontent.com/54324782/146661479-aa122cb2-c556-4184-9f3b-9259b975a4ff.png)
  

- 여러 옵셔널 변수들을 한꺼번에 바인딩할 수도 있다.

```swift
var myName: String? = "yoonhee"
var yourName: String? = nil

//if let name = myName, let friend = yourName {
    // print("\(name) and \(friend)") // yourName이 nil이기 때문에 실행되지 않는다.
//}

yourName = "hana" // yourName에 값 할당

if let name = myName, let friend = yourName {
    print("\(name) and \(friend)") 
}

```
![결과](https://user-images.githubusercontent.com/54324782/146661501-ff639060-2914-4601-81d2-6777a33b56f3.png)


------------------

## 2. 강제 추출 (Force Unwrapping)

- 옵셔널의 값을 강제로 추출한다.

```swift
func printName(_ name: String) {
    print(name)
}

var myName: String? = "yoonhee"

printName(myName!) // 느낌표(!)를 통해 강제 추출

myName = nil
//print(myName!) // 강제추출 시 값이 없으므로 런타임 오류 발생

var yourName: String! = nil
// 암시적 추출 옵셔널 형식은 느낌표를 붙이지 않아도 알아서 느낌표를 붙여준 것과 같은 효과를 보여주므로 전달이 가능하다
print(yourName) // nil 값이 전달되기 때문에 런타임 오류 발생

```

- 좀 더 안전하게 옵셔널을 사용하기 위해서는 옵셔널 바인딩을 사용하는 것이 좋다.

-------------------
출처 : [Swift 문법강좌](https://www.youtube.com/playlist?list=PLz8NH7YHUj_ZmlgcSETF51Z9GSSU6Uioy)

