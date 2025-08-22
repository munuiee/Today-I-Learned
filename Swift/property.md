# Property
`class`, `struct`, `enum` 등에서 사용되는 변수나 상수

<br>

## 저장 프로퍼티 Stored Property
데이터를 저장하는 프로퍼티
- `var`와 `let` 모두 사용 가능
- `class`, `struct` 등에서 데이터를 저장하기 위한 변수와 상수
- `enum`에서는 저장 프로퍼티 사용 불가 (빌드 오류 발생)
- 초깃값을 가질 수 있다
- 초기화 필수! 기본값을 주거나 `init`에서 넣기

```swift
struct Person {
	var name: STtring // 값을 저장하는 저장 프로퍼티
    var age: Int = 0 // 값을 저장하는 초깃값이 있는 저장 프로퍼티
}
```

<br>
<br>


## 연산 프로퍼티 Computed Property
값을 직접 저장하지 않고 계산된 값을 제공하는 프로퍼티
계산해서 값을 주거나(`set`), 가져오거나(`get`)하는 프로퍼티
- `class`, `struct`, `enum` 등에서 사용 가능
- `var`만 사용 가능 (동적으로 계산하여 값을 반환)
- `getter`와 `setter`를 사용하여 동적으로 값 계산
	-
    - `getter`: `get` 키워드를 사용하여 코드블록을 구현
    - `setter`: `set` 키워드를 사용하여 코드블록 구현
- `getter`은 필수
- `setter`을 구현하지 않았다면 `get` 키워드 생략 가능
<br>

### `get`
- 값을 가져올 때 동작
- 값을 리턴해야 함
- 생략 가능
```swift
var nameLength: Int {
	return name.count // get 생략 가능
}
```
```swift
var nameLength: Int {
	get {
    	return name.count
    }
}
```
💁🏻‍♀️ 참고! `get`만 있으면 읽기 전용 프로퍼티



<br>

### `set`
- 값을 설정할 때 동작
- 자동으로 `newValue`라는 이름의 값이 들어옴
- 원하면 `set(커스텀이름)` 이렇게 이름 지정 가능

```swift
var score: Int = 0

var level: Int {
	get {
    	return score / 10
    }
    
    set {
    	score = newValue * 10
    }
}
```

💠 `newValue` 대신 커스텀 이름 쓰기
```swift
var volume: Int {
	get {
    	return 10
    }
    set(value) {
    	print("새로운 값은 \(value)")
    }
}
```



<br>

💠 `getter`와 `setter` 모두 있는 연산 프로퍼티
```swift
struct Person {
	var name: String
    var age: Int = 0
    
    ver isAdult: Bool { // getter와 setter을 제공하는 연산 프로퍼티
    	get {
        	return age >= 20 
        }
        
        set {
        	if newValue == true { // newValue는 새로 할당한 값
            age = 20
        } else {
        	age = 19
       }
     }
  }
}

var person = Person(name: "Jihye", age: 21)

print(person.isAdult) // age가 20보다 크므로 isAdult는 true가 됨
person.isAdult = false // set 코드블록이 실행되어 age를 19로 변경시킴
print(person.age) // 19
```

💠 `setter`가 구현되지 않은 연산 프로퍼티
```swift
struct Person {
	var name: String // 값을 저장하는 저장 프로퍼티
    var age: Int = 0 // 값을 저장하는 초깃값이 있는 저장 프로퍼티
    
    var isAdult: Bool {
    	get {
        	return age >= 20
        }
    }
}

var person = Person(name: "Jihye", age: 100)
print(person.isAdult) // true
person.isAdult = false // Error. isAdult에는 getter만 있기 때문에 새로운 값 할당 불가능

```

💠 `setter`가 구현되지 않았을 땐 `get` 키워드 생략 가능 
```swift
struct Person {
	var name: String
    var age: Int = 0
    
    var isAdult: Bool // get 키워드가 생략된 연산 프로퍼티
    	return age >= 20
    }
}
```

<br>
<br>

## 타입 프로퍼티 Type Property
모든 인스턴스가 공유하는 프로퍼티, 인스턴스를 만들지 않고 타입 자체에서 접근이 가능
- `static` 키워드를 사용
- `class`, `enum`, `struct` 사용 가능
- `타입이름.타입프로퍼티_이름` 형태로 접근
- `static` 키워드로 선언 (오버라이드 불가)
- 오버라이딩 허용 👉 클래스에서만 `class` 키워드 써도 됨
```swift
struct Person {	
	static var structName = "Person"
    
    func logStructName() {
    	print(Person.structName) 
    }
}

var person = Person()
person.logStructName() // Person
Person.structName = "Changed!"
person.logStructName() // Changed!
print(Person.structName) // Changed!
```

💠 `enum`에서 사용하기
```swift
enum Season: String {
	case spring
    case summer
    case autumn
    case winter
    
    static var enumName = "Season"
}

Season.enumName // Season
```

<br>
<br>

## 프로퍼티 옵저버 Property Observers
`저장 프로퍼티`의 값이 변경되는 것을 감시하고 있다가 코드블록을 실행할 수 있는 기능
- `저장 프로퍼티` 타입 뒤에 코드블록을 작성하여 생성
- `저장 프로퍼티`가 사용 가능한 `struct`, `class`에서 사용 가능
- `willSet`, `didSet`을 제공. 둘 중 하나만 작성해도 OK

### `willSet`
- 값이 변경되기 전에 호출
- 변경될 값은 `newValue`를 통해 접근하며, 이름을 정할 수 있음
- 이름을 정하려면 `willSet(이름)` 형식으로 작성

<br>

### `didSet`
- 값이 변경된 후 호출
- 변경되기 전의 값은 `oldValue`를 통해 접근하며, 이름을 정할 수 있음
- 이름을 정하려면 `didSet(이름)` 형식으로 작성

```swift
struct Person {
	var name: String {
    	willset {
       	    print("Person의 name이 변경될 예정입니다. 변경될 값은 \"\(newValue)\" 입니다.")
        }
        
        didSet {
        	print("Person의 name이 변경되어 didSet 코드블록이 호출되었습니다.")
            print("\(oldValue) -> \(name)")
        }
   }
   var age: Int
}

var person = Person(name: "Jihye", age: 10)

person.anme = "Apple"


/* 출력 값
Person의 name이 변경될 예정입니다. 변경될 값은 "Apple" 입니다.
Person의 name이 변경되어 didSet 코드블록이 호출되었습니다.
Jihye -> Apple
*/
```

💠 이름 변경해서 사용
```swift
struct Person {
	var name: String {
    	willSet(changeNewName) {
        	 print("Person의 name이 변경될 예정입니다. 변경될 값은 \"\(changeNewName)\" 입니다.")
        }
        
        didSet(beforeName) {
            print("Person의 name이 변경되어 didSet 코드블록이 호출되었습니다.")
            print("\(name) -> \(beforeName)")
        }
    }
    var age: Int
}
```

<br>
<br>

## 지연 저장 프로퍼티 Lazy Stored Property
처음 사용하기 전까지 실제로 메모리에 값을 저장하지 않는 지연된 저장 프로퍼티
- 사용하기 전까지 값을 저장하지 않기 때문에 메모리 효율을 높일 수 있음
- `lazy` 키워드 사용 `lazy var 프로퍼티이름`
- `var`에서만 사용 가능
- `class`, `struct` 사용

```swift
class Person {
	var name: String = "A"
    var age: Int = 15
    lazy var height
}

let person = Person()
// Person의 height 값에 접근하지 않았기 때문에 아직 메모리에 할당되지 않은 상태
print(person.height) // height 값을 사용하기 때문에 이제 메모리에 할당

struct Animal {
	var name: String
    var age: Int
    lazy var color: String = "Black"
}

var animal = Animal(name: "Dog", age: 10) // color값에 접근하지 않았기 때문에 아직 메모리에 할당되지 않은 상태
print(animal.color) // color값을 사용하기 때문에 이제 메모리에 할당하여 사용함
```
