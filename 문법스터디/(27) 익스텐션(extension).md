## 1. 익스텐션 (extension)

- 익스텐션은 구조체, 클래스, 열거형, 프로토콜 타입에 새로운 기능을 추가할 수 있는 기능이다.
- 기능을 추가하려는 타입의 구현된 소스 코드를 알지 못하거나 볼 수 없다해도, 타입만 알고 있다면 그 타입의 기능을 확장할 수도 있다.

- 익스텐션으로 추가할 수 있는 기능  
> 연산 타입 프로퍼티 / 연산 인스턴스 프로퍼티  
> 타입 메서드 / 인스턴스 메서드  
> 이니셜라이저  
> 서브스크립트  
> 중첩 타입  
> 특정 프로토콜을 준수할 수 있도록 기능 추가  

- 기존에 존재하는 기능을 재정의할 수는 없다.

#### 정의 문법

    extension 확장할 타입 이름 {
        /* 타입에 추가될 새로운 기능 구현 */
    }
    
    // 익스텐션은 기존에 존재하는 타입이 추가적으로 다른 프로토콜을 채택할 수 있도록 확장할 수도 있다.
    extension 확장할 타입 이름: 프로토콜1, 프로토콜2, 프로토콜3... {
        /* 프로토콜 요구사항 구현 */
    }


------------------

## 2. 익스텐션 구현

#### 연산 프로퍼티 추가

```swift
extension Int {
    var isEven: Bool {
        return self % 2 == 0
    }
    var isOdd: Bool {
        return self % 2 == 1
    }
}

print(1.isEven) // false
print(2.isEven) // true
print(1.isOdd) // true
print(2.isOdd) // false

var number: Int = 3
print(number.isEven) // false
print(number.isOdd) // true

number = 2
print(number.isEven) // true
print(number.isOdd) // false

```
![결과](https://user-images.githubusercontent.com/54324782/147424290-621d38f2-224b-4c43-8dd0-6b9d4aeb9c8c.png)

#### 메서드 추가

```swift
extension Int {
    func multiply(by n: Int) -> Int {
        return self * n
    }
}

print(3.multiply(by: 2)) // 6
print(4.multiply(by: 5)) // 20

number = 3
print(number.multiply(by: 2)) // 6
print(number.multiply(by: 3)) // 9

```
![결과](https://user-images.githubusercontent.com/54324782/147424385-eeb7d47b-6d69-4b2a-b6a3-1c197049a28d.png)

#### 이니셜라이저 추가

```swift
extension String {
    init(intTypeNumber: Int) {
        self = "\(intTypeNumber)"
    }
    
    init(doubleTypeNumber: Double) {
        self = "\(doubleTypeNumber)"
    }
}

let stringFromInt: String = String(intTypeNumber: 100) 
print(stringFromInt) // "100"

let stringFromDouble: String = String(doubleTypeNumber: 100.0) 
print(stringFromDouble) // "100.0"

```
![image](https://user-images.githubusercontent.com/54324782/147424486-4a90f383-766c-4af2-9755-b451259754d9.png)


-------------------
출처 : [Swift 문법강좌](https://www.youtube.com/playlist?list=PLz8NH7YHUj_ZmlgcSETF51Z9GSSU6Uioy)

