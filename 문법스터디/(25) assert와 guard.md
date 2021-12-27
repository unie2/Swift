## 1. assert와 guard

- 애플리케이션이 동작 도중에 생성하는 다양한 결과값을 동적으로 확인하고 안전하게 처리할 수 있도록 확인하고 빠르게 처리할 수 있다.

#### Assertion

- assert(\_:\_:file:line:) 함수를 사용한다.
- assert 함수는 디버깅 모드에서만 동작한다.
- 배포하는 애플리케이션에서는 제외된다.
- 주로 디버깅 중 조건의 검증을 위하여 사용한다.

```swift
var someInt: Int = 0

assert(someInt == 0, "someInt != 0") // someInt 값이 0이면 지나치고, 아니라면 두번째 매개변수 메시지를 출력한 후 동작 중지

someInt = 1
//assert(someInt == 0) // 동작 중지, 검증 실패
//assert(someInt == 0, "someInt != 0") // 동작 중지, 검증 실패
// assertion failed: someInt != 0: file guard_assert.swift, line 12

func functionWithAssert(age: Int?) {
    assert(age != nil, "age == nil")
    
    assert((age! >= 0) && (age! <= 130), "나이값 입력이 잘못되었습니다.")
    print("당신의 나이는 \(age!)세입니다.")
}

functionWithAssert(age: 50)
//functionWithAssert(age: -1) // 동작 중지, 검증 실패
//functionWithAssert(age: nil) // 동작 중지, 검증 실패

```
![결과](https://user-images.githubusercontent.com/54324782/147422714-661480da-eb22-4e05-ba24-19a1dc076de9.png)


------------------

## 2. Early Exit

- guard를 사용하여 잘못된 값의 전달 시 특정 실행구문을 빠르게 종료한다.
- 디버깅 모드 뿐만 아니라 어떤 조건에서도 동작한다.
- guard의 else 블럭 내부에는 특정 코드블럭을 종료하는 지시어(return, break 등)가 꼭 있어야 한다.
- 타입 캐스팅, 옵셔널과도 자주 사용된다.
- 그 외 단순 조건 판단 후 빠르게 종료할 때도 용이하다.


```swift
func functionWithGuard(age: Int?) {
    guard let unwrappedAge = age, // guard let을 통해 옵셔널 바인딩 먼저 수행, age가 nil이라면 실행 안되고 return됌
        unwrappedAge < 130,
        unwrappedAge >= 0 else { // guard에는 else가 꼭 따라 붙음
        print("나이값 입력이 잘못되었습니다.")
        return // return을 명시해주지 않으면 컴파일러 오류 발생
    }
    print("당신의 나이는 \(unwrappedAge)세입니다.")
}

```

- 반복문 내에서도 사용할 수 있다.

```swift
var count = 1

while true {
    guard count < 3 else {
        break
    }
    print(count)
    count += 1
}

```
![결과](https://user-images.githubusercontent.com/54324782/147422864-297301ad-1c75-4e9a-af2c-cd1cb422c997.png)
  
- 딕셔너리를 받아왔을 때 굉장히 많이 활용한다.

```swift
func someFunction(info: [String: Any]) {
    guard let name = info["name"] as? String else { // 딕셔너리에서 나오는 값들은 모두 옵셔널이다.
        return
    }
    
    guard let age = info["age"] as? Int, age >= 0 else {
        return
    }
    
    print("\(name): \(age)")
}

someFunction(info: ["name": "jenny", "age": "10"]) // age가 String 타입이므로 return
someFunction(info: ["name": "mike"]) // age가 없어 바인딩, 캐스팅 모두 되지 못하므로 return
someFunction(info: ["name": "yoonhee", "age": 10]) // 정상 출력

```
![결과](https://user-images.githubusercontent.com/54324782/147423023-f4fe871f-7f8b-497d-b5d3-64996d94f11c.png)


-------------------
출처 : [Swift 문법강좌](https://www.youtube.com/playlist?list=PLz8NH7YHUj_ZmlgcSETF51Z9GSSU6Uioy)

