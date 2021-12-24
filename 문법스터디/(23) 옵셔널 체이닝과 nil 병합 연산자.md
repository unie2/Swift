## 1. 옵셔널 체이닝

- 옵셔널 체이닝은 옵셔널 요소 내부의 프로퍼티로 또다시 옵셔널이 연속적으로 연결되는 경우 유용하게 사용할 수 있다.

```swift
class Person {
    var name: String
    var job: String?
    var home: Apartment?
    
    init(name: String) {
        self.name = name
    }
}

class Apartment {
    var buildingNumber: String // 동
    var roomNumber: String // 호수
    var `guard`: String? // 경비원
    var owner: Person? // 집주인
    
    init(dong: String, ho: String) {
        buildingNumber = dong
        roomNumber = ho
    }
}

let yoonhee: Person? = Person(name: "yoonhee")
let apart: Apartment? = Apartment(dong: "101", ho: "202")
let superman: Person? = Person(name: "superman")

```

- 옵셔널 체이닝이 실행 후 결과값이 nil일 수 있으므로 결과 타입도 옵셔널이다.

```swift
// 옵셔널 체이닝을 사용하지 않는다면 ...
func guardJob(owner: Person?) {
    if let owner = owner {
        if let home = owner.home {
            if let `guard` = home.guard {
                if let guardJob = `guard`.job {
                    print("우리집 경비원의 직업은 \(guardJob)입니다.")
                } else {
                    print("우리집 경비원은 직업이 없어요.")
                }
            }
        }
    }
}

guardJob(owner: yoonhee)

// 옵셔널 체이닝을 사용한다면 !
func guardJobWithOptionalChaining(owner: Person?) {
    if let guardJob = owner?.home?.guard?.job {
        print("우리집 경비원의 직업은 \(guardJob)입니다.")
    } else {
        print("우리집 경비원은 직업이 없어요.")
    }
}

guardJobWithOptionalChaining(owner: yoonhee)


yoonhee?.home?.guard?.job // nil (yoonhee에 집이 할당되어 있지 않다.)

yoonhee?.home = apart // 할당

yoonhee?.home // Optional(Apartment)
yoonhee?.home?.guard // nil (집이 있지만, 경비원이 없다.)

yoonhee?.home?.guard = superman // 할당

yoonhee?.home?.guard // Optional(Person)

yoonhee?.home?.guard?.name // superman
yoonhee?.home?.guard?.job // nil (직업이 할당되어 있지 않다.)

yoonhee?.home?.guard?.job = "경비원"

```

#### nil 병합 연산자

```swift
var guardJob: String

guardJob = yoonhee?.home?.guard?.job ?? "슈퍼맨" // 앞에 값이 nil이라면 "슈퍼맨"을 guardJob에 할당
print(guardJob)

yoonhee?.home?.guard?.job = nil

guardJob = yoonhee?.home?.guard?.job ?? "슈퍼맨"
print(guardJob)

```
![결과](https://user-images.githubusercontent.com/54324782/147306095-433e6d7b-5023-416f-9442-bdc67933bf7d.png)


-------------------
출처 : [Swift 문법강좌](https://www.youtube.com/playlist?list=PLz8NH7YHUj_ZmlgcSETF51Z9GSSU6Uioy)

