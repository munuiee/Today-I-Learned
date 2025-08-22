# 중첩 타입 Nested Type
하나의 타입 안에 다른 타입을 정의

<br>

- 구조적으로 복잡한 클래스나 구조체 등을 더 조직적으로 관리 가능
- `class`, `struct`, `enum` 등에서 사용
- 중첩된 타입을 사용하면 코드의 가독성을 높이고 타입 간의 연관성을 명확히 할 수 있다.
- 타입의 블록 안에서 다른 타입을 정의하고 사용하는 방식으로 구현

```swift
struct Car {
  struct Company  {
    var name: String
    var phoneNumber: String

    func contact() {
        print("\(name) 회사의 A/S 센터 번호는 \(phoneNumber)입니다.")
    }
  }

  enum Model {
      case sedan
      case hatchback
      case suv
  }

  var model: Model
  var company: Company
  var name: String
  var color: String
}

let myCar =  Car(model: .sedan,
                company: Car.company(name: "스파르타!", phoneNumber: "000-0000-0000"),
                name: "붕붕이",
                color: "Black"

myCar.company.contact() // 스파르타! 회사의 A/S 센터 번호는 000-0000-0000입니다.
print(myCar.model) // model의 프로퍼티 출력
```

