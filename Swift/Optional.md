# Optional

```swift
struct Person {
	var name: String
    var age: Int
    var car: String // 모든 사람이 자동차를 갖고 있는가?
    
    func introduce() {
    	print("안녕하세요. 제 이름은 \(name)이고, 나이는 \(age)살입니다.")
    }
}

```

- Swift는 기본적으로 `nil(값없음)`을 헝용하지 않지만 개발을 하다보면 값이 없는 경우가 생기게 된다.
👉 이럴 때 사용하는 것이 `Optional`이다.

```swift
struct Person {
	var name: String
    var age: Int
    var car: String?
    
    func introduce() {
    	print("안녕하세요. 제 이름은 \(name)이고, 나이는 \(age)살입니다.")
    }
}
```
<br>

- `nil` 키워드는 `값이 없음`을 의미
- 값이 없을 수 있는 상태를 `옵셔널`이라고 하며, 옵셔널 타입은 `nil`로 저장할 수 있다.
- 기존 타입 뒤에 `?`를 붙인다.
	
    - 기본 타입 (Int, String, Float)
    - Collection Type (Array, Set, Dictionary)
    - Custom Type (`struct`, `class`, `enum`)
    - 익명함수인 `클로저`
- 값을 할당할 때는 기존의 타입과 동일하게 사용
- 옵셔널 타입의 값에 접근하면 `Optional`로 감싸진 것이 나오는데, 이를 `Optional로 래핑된 값`이라고 부른다.

<br>

## 선언 방법
```swift
💠 기본 타입 옵셔널 선언
var intValue: Int?
var stringValue: String?

💠 Collection Type 옵셔널 선언
var array: [String]?
var dictionary: [String: String]?

💠 Custom Type 옵셔널 선언
struct Person {
	let name: String
}

var optionalPerson: Person?

💠 클로저 옵셔널 선언
var closure: (() -> Void)?
```

<br>

## 사용 방법
```swift
//값을 할당할 때는 기존의 타입과 동일하게 사용
var intValue: Int? = 1

var stringValue: String?
stringValue = "안녕하세요"

var nilValue: String? = nil

struct Person {
	let name: String
}

var optionalPerson: Person? = Person(name: "Jihye")

var closure: (() -> Void)? = {
	print("Fire")
}

// 값에 접근하면 Optional로 래핑된 값이 나옴
print(intValue) // Optional(1)
print(stringValue) // Optional("안녕하세요")
print(nilValue) // nil
```

<br>

### 기본 타입과 연산 불가능
`옵셔널 타입`과 `기본타입`은 다른 타입이기 때문에 연산이 불가능하다.
- 비교 연산자 사용 가능

```swift
var intValue: Int? = 5

intValue += 5 // Error
```
- 옵셔널 언래핑 작업을 통해 기본 타입으로 변환하여 사용해야 함

<br>
<br>

## 옵셔널 체이닝 Optional Chaining
옵셔널 타입을 포함하는 복잡한 데이터 구조에서 옵셔널 값이 `nil`인지를 간결하게 체크하고 접근할 수 있는 방법
- 여러 중첩된 프로퍼티나 메소드 호출을 한줄로 처리할 수 있으며, 중간에 `nil`이 있는 경우 자동으로 `nil`을 반환
- 옵셔널 체이닝은 옵셔널 값에 대해 접근할 때마다 안전하게 처리 가능
- 옵셔널 값에 접근할 때 프로퍼티나 메서드 이름 뒤에 `?`를 붙여서 체이닝

```swift
struct Person {
	var name: String = "Default Name"
    var animal: Animal? // 반려동물이 있을수도, 없을수도 있다
}

struct Animal {
	let name: String
    var age: Int? // 언제 태어났는지 모를 경우
}

let person: Person? = Person(name: "Jihye", animal: nil)
print(person?.animal?.name) // nil - person은 옵셔널 값이어서 ?가 붙으며 animal?은 nil이므로 nil이 반환됨

let person2: Person(name: "Jihye", animal: Animal(name: "Dog", age: 5))
print(person2.animal?.name) // Optional("Dog")
```

```swift
let stringValue: String? = "안녕하세요"
print(stringValue?.count) // Optional(5)
```

<br>

`pseron?.animal?.name`
- 옵셔널 값에 `?`를 붙인 후 `.`을 사용하면 중첩된 프로퍼티나 메서드에 접근
- 중첩된 값 중 하나라도 `nil`이면 전체값을 `nil`로 반환
- 중첩된 값이 모두 `nil`이 아니라면 `Optional`로 래핑된 값 반환
