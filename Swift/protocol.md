# 프로토콜 Protocol
프로토콜 자체는 기능을 구현하지 않으며 오직 설계만 제공한다.
- `class`, `struct`, `enum`에서 프로토콜을 채택할 수 있으며, 프로토콜에서 정의한 프로퍼티와 메소드를 모두 구현해야 한다.

#### 프로토콜을 채택하는 방법
- 타입의 이름 뒤에 `:` 콜론을 넣은 후 프로토콜 이름 작성
- 프로토콜은 여러 개를 채택할 수 있으며, 프로토콜 이름을 `,`로 구분한다.

- 프로토콜에서 정의된 프로퍼티는 항상 `var`로 선언되어야 한다.
- 프로토콜에서 정의하는 프로퍼티는 읽기 전용 `{ get }` 또는 읽기-쓰기 가능 `{ get set }`으로 설정할 수 있다.
	
    - `{ get }`으로만 설정해도 프로퍼티의 값을 변경할 수 있지만, 명시적으로 작성하면 코드의 의도를 쉽게 파악 가능
- 프로토콜에서 정의하는 메소드는 `이름`, `파라미터`, `리턴타입`만 선언하며, 구현부 `{ }`는 작성하지 않는다.

<br>

### 기본 정의 방법
```swift
protocol 프로토콜이름 {
	// 프로퍼티 정의
    // 메서드 정의
}

protocol FullyNamed {
	var fullName: String { get }
    
    func sayMyFullName() -> String // 구현부는 작성하지 않음
}

```

<br>

### 프로토콜을 채택하여 구현하기

💠 한 개의 프로토콜 채택
```swift

protocol FullyNamed {
	var fullName: String { get }
    
    func sayMyFullName() -> String
}

class Person: FullyNamed { // FullyName 프로토콜 채택
	var fullName: String // FullyName 프로토콜에 있는 fullName 프로퍼티를 구현
    
    func sayMyFullName() -> String { // 프로토콜에 있는 메서드 구현
    	return fullName
    }
    
    init(fullName: String) {
    	self.fullName = fullName
    }
}

var person = Person(fullName: "Jihye")

print(person.fullName) // Jihye
print(person.sayMyFullName()) // Jihye
```

<br>

💠 여러개의 프로토콜 채택
```swift
protocol FullyNamed {
	var fullName: String { get }
    
    func sayMyFullName() -> String
}

protocol shortNamed {
	var shortName: String { get }
}

clas Person: FullyNamed, ShortNamed { // 프로토콜 여러개를 채택하는 클래스
	var fullName: String
    
    func sayMyFullName() -> String {
    	return fullName
    }
    
    var shortName: String {
    	return "ShortName"
    }
    
    init(fullName: String) {
    	self.fullName = fullName
    }
}

var person = Person(fullName: "Jihye")

print(person.fullName) // Jihye
print(person.sayMyFullName()) // Jihye
print(person.shortName) // ShortName
```

<br>

### `class` 전용 프로토콜 만들기
- `struct`, `enum`에서 사용될 수 없다.
- 프로토콜 정의 시, AnyObject를 채택하면 클래스 전용 프로토콜로 만들 수 있다.
```swift
protocol OnlyClassProtocol: AnyObject {

}
```
