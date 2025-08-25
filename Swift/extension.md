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
```

##  이미 있는 설계도에 기능을 추가하면 되지 않을까?
`extension`이 따로 있는 이유

### 1. 내가 만든 클래스/구조체가 아닐 때
`Int`, `String`, `Double`, `Array`는 애플이 Swift 언어 안에 이미 만들어놓은 타입들. <br>
그래서 우리가 직접 고쳐서 `Int` 안에 새 기능을 추가하는 건 불가능하다.

<br>


### 2. 코드 정리 
클래스 기능이 너무 많아지면 보기 힘듦.
이럴 때 `extension`으로 관리하면 깔끔해짐
```swift
class Dog {
    var name: String = ""
}

// 짖는 기능
extension Dog {
    func bark() {
        print("멍멍!")
    }
}

// 훈련 기능
extension Dog {
    func sit() {
        print("\(name)이 앉았다!")
    }
}

```

<br>

### 3. 저장 속성 추가 불가 (안전성)
- 저장 속성(메모리 차지하는 변수)은 못 넣음.
