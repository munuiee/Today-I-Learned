# extension
기존 타입이나 클래스, 구조체, 열거형에 새로운 기능을 **확장**해서 붙여주는 도구 <br>
👉 이미 만들어져 있는 타입에 새로운 메서드, 계산 속성, 이니셜라이저 등을 덧붙이는 것

- 하나의 프로토콜을 `extension`으로 추가해 적용할 수 있다.
	
    - 이를 통해 기존 타입을 수정하지 않고 프로토콜 요구사항을 구현할 수 있어 코드 유지보수가 편리해짐
- 하나의 타입에 `extension` 여러 번 가능
- 확장할 수 있는 것들
	
    - 연산 프로퍼티
    	- 확장된 곳에서 저장 프로퍼티는 사용 불가
    - 메서드
    - 새로운 초기화 `init`
    - 중첩된 타입(Nested Type)
    
    
### 사용 방법
```swift
struct Person {
	let name: String
}

// extension 키워드 작성 후 확장시키고 싶은 타입 이름 명시
extension Person {

}

// 특정 타입의 프로토콜을 확장시키고 싶을 때
extension Person: Equatable {

}
```

<br>
 

#### 확장할 수 있는 것들
```swift
struct Person {	
	let lastName: String
    let firstName: String
    let age: Int
}

protocol FullyNamed {
	var fullName: String { get }
    
    func sayMyFullName() -> String
}

// extenstion에서 연산 프로퍼티 구현
extension Person {
	var nameAge: String {
    	return "\(firstName)(\(age)세)"
    }
}

// extension에서 메서드 구현
extension Person {
	func sayHello() {	
    	print("\(firstName)님 안녕하세요?")
    }
}

// extension에서 Protocol 채택하여 구현
extension Person: FullyNamed {
	var fullName: String {
    	return "(\(lastName)\(firstName)"
    }
	
    func sayMyFullName() -> String {
    	return "제 이름은 \(fullName) 입니다."
    }
}

let person = Person(lastName: "홍" ,firstName: "길동", age: 20)

print(person.nameAge) // 길동(20세)
person.sayHello() // 길동님 안녕하세요?
print(person.fullName) // 홍길동 
print(person.sayMyFullName()) // 제 이름은 홍길동입니다.
