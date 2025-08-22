# Struct
연관된 상태는 변수, 상수에 저장하고 행동은 함수를 정의한 후 그룹화하여 `데이터타입`으로 사용

<br>

## 특징
- `프로퍼티`와 `메소드`로 구성
- 구조체의 인스턴스르 생성하여 사용
- 구조체 안에서 사용되는 변수와 상수인 프로퍼티에는 `default` 값을 정해줄 수 있음
- Memberwise Initializer(멤버와이즈 이니셜라이저)를 제공
	
    - 직접 `init`을 정의하지 않아도 모든 프로퍼티의 초기화를 자동으로 생성해주는 기능
- 구조체를 사용하여 만들어진 인스턴스는 `Value Type`
	
    - 구조체의 인스턴스는 값이 복사 되므로, 서로 다른 값으로 처리됨
- 메소드에서 프로퍼티를 변경하려면 `mutating` 키워드를 사용
- `상속` 불가능
- 인스턴스를 `let`으로 만들면 내부 프로퍼티 변경 불가

<br>

### 기본 정의
```swift
struct 구조체이름 {
	// 프로퍼티 선언
    // 함수 구현
    
    // init을 만들지 않아도 자동으로 만들어줘서 생략해도 된다!
}

```

<br>

### 초기화 방법
- 모든 프로퍼티의 값을 할당해주어야 한다.
	
    - `값이 없을 수 있는 옵셔널 타입`, `초기값을 준 프로퍼티`는 예외
    - `init`을 여러개 생성 가능
    - Memberwise init 제공
    

<br>

1️⃣ `memberwise init` 사용
- 자동으로 `init` 생성
```swift
struct Person {
	var name: String
    var age: Int
}

var person = Person(name: "Jihye", age: 26)
```
- 기본값을 할당한 프로퍼티가 있을 때 멤버와이즈 init은 생략하고 만들어줌

```swift
struct Person {
	var name: String
    var age: Int = 0
}

Person(name: "Jihye")
Person(name: "Jihye", age: 26)
```

<br>

2️⃣ 기본값 초기화
```swift
struct Person {
	var name: String = "이름없음"
    var age: Int = 1
]

Person() // 기본값만 사용 가능
Person(name: "Jihye") // 이름만 변경하고 age는 기본값
Person(age: 26) 
Person(name: "Jihye", age: 26)
```

<br>

3️⃣ 지정 초기화
- `init`을 직접 생성하면 `memberwise init`이 사용되지 않음
```swift
struct Person {
	var name: String = "이름없음"
    var age: Int = 1
    
    init() {
    	print("init")
    }
}

Person() // 정상동작: Person에서 init()을 구현했으므로
Person(name: "Jihye") // Error: name만을 파라미터로 받는 init 없음
Person(age: 26) // Error
Person(name: "Jihye", age: 26) // Error: name, age를 파라미터로 받는 init이 없음
```

<br>

4️⃣ 여러개의 `init` 사용
```swift
struct Person {
	var name: String
    var age: Int
    
    init() {
    	self.name = "이름 없음"
    	self.age = 0
    }
    
    init(name: String) {
    	self.name = name
        self.age = 0
    }
    
    init(name: String, age: Int) {
    	self.name = name
        self.age = age
    }
}

Person() 
Person(name: "Jihye") 
Person(age: 26) // // Error : 파라미터로 age만 전달하는 init이 없기떄문에 컴파일 오류 발생
Person(name: "Jihye", age: 26)

```
