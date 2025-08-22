# Method
`class`, `struct`, `enum` 등에서 사용되는 함수
- 인스턴스 메서드
- 타입 메서드

<br>

## 인스턴스 메서드 Instance Method
인스턴스를 통해서 호출
```swift
class Person {
	var name: String = "Default Name"
    var age: Int = 15
    
    func introduce() -> String {
    	return "안녕하세요. 제 이름은 \(name)이고, 나이는 \(age)살입니다."
    }
    
    func printIndtroduce() {
    	print(introduce())
    }
}

let person = Person()
print(person.introduce())
person.printIndtroduce()

```
#### 인스턴스 메서드에서 프로퍼티 변경하기
인스턴스가 `Reference Type`, `Value Type`에 따라서 프로퍼티를 변경하는 방법이 나누어짐

<br>

### Reference Type
`class`로 만들어진 `인스턴스`는 `Reference Type`이므로 인스턴스 메서드에서 프로퍼티 값을 직접 변경 가능
```swift
class Person {
	var name: String = 'Default Name"
    var age: Int = 15
    
    func introduce() -> String {
    	return "안녕하세요. 제 이름은 \(name)이고, 나이는 \(age)살입니다.
        
    func timeToNextYear() {
    	age += 1
    }
}

let person = Person()
print(person.age) // 15
person.tiemToNextYear() // 16
print(person.age) // 16
```
<br>

### Value Type
`struct`, `enum`은 `value type`이므로, 인스턴스 메서드에서 프로퍼티를 직접 변경할 수 없으며 수정하려면 `mutating` 키워드를 사용해야 한다.
```swift
struct Person {
	var name: String = "Default Name"
    var age: Int = 15
    
    func introduce() -> String {
    	return "안녕하세요. 제 이름은 \(name)이고, 나이는 \(age)살 입니다."
    }
    
    mutating func timeToNextYear() { // mutating을 붙이지 않으면 컴파일 오류 발생
    	age += 1
    }
}

var person = Person()
print(person.age) // 15
person.timeToNextYear() // 16
print(person.age) // 16
```

💠 `enum` 메서드에서 값 변경하기
```swift
enum VideoPlayerState {
	case off
    case playing
    case complete
    
    mutating func moveNext() {
    	switch self {
        case .off:
        	self = .playing
        case .playing:
        	self = .complete
        case .complete:
        	self = .off
        }
    }
}

var playerState = VideoPlayerState.off
print(playerState) // off

playerState.moveNext()
print(playerState) // playing

playerState.moveNext()
print(playerState) // completed
```

<br>
<br>

## 타입 메서드 Type Method
`타입 프로퍼티`와 마찬가지로 인스턴스를 만들지 않고 호출
- `static` 키워드 사용
- `class`, `struct`, `enum` 등에서 사용
- 함수 내부에 있는 타입 프로퍼티에만 접근 가능. 인스턴스를 만들지 않고 사용하기 때문에 다른 프로퍼티에는 접근 불가

💠 `struct`, `class`에서 타입 메서드 사용 방법
```swift
struct Person {
	static var structName = "Person"
    var name: String = "Default Name"
    var age: Int = 15
    
    func introduce() -> String {
    	"안녕하세요. 제 이름은 \(name)이고, 나이는 \(age)살 입니다."
    }

    static func introduceType() -> String {
    // name = "A" // 오류 발생! 저장 프로퍼티에는 접근할 수 없음!
        return "안녕하세요. 저는 \(structName) 타입입니다."
    }
}

print(Person.introduceType()) // 출력 값 : 안녕하세요. 저는 Person 타입입니다.
```

💠 `enum`에서 타입 메서드 사용 방법
```swift
enum Season {
    static var enumName = "Season"
    case spring
    
    static func introduceType() -> String {
        return "저는 \(enumName) 타입입니다."
    }
}

print(Season.introduceType())
```

