# class
연관된 상태는 변수, 상수에 저장하고 행동은 함수를 정의한 후 그룹화하여 `데이터타입`으로 사용할 수 있다.

<br>

## 특징
- `프로퍼티`와 `메소드`로 구성
	
    - `프로퍼티`: 구조체, class 안에 있는 변수 , 상수
    - `메소드`: 구조체, class 안에 있는 함수
- class의 인스턴스를 생성하여 사용
- class 안에서 사용되는 변수와 상수인 `프로퍼티`에는 `default` 값을 정해줄 수 있음
- class의 인스턴스를 생성할 때 반드시 초기화를 해주어야 함
- `init` 초기화를 제공
	
    - 모든 프로퍼티에 default 값을 제공한다면 `init` 초기화 생략 가능
    - 모든 프로퍼티가 `Optional`인 경우 `init` 초기화 생략 가능
- 초기화를 도와주는 컨비니언스 이니셜라이저(Convenience Initaializer)를 제공
- class를 사용해서 만들어진 인스턴스는 `Reference Type`이다.
	
    - 인스턴스를 `let`으로 만들어도 프로퍼티 변경이 됨
    - 함수에 class의 인스턴스를 전달하고 프로퍼티를 변경하면 원본도 변경됨
- `상속` 가능
	
    - 하위클래스가 상위클래스의 속성(프로퍼티)와 행동(메소드)를 물려받아서 사용 가능
    
<br>
<br>

### 기본 정의 방법
```
class 클래스이름 {
	// 파라미터 선언
    // 메소드 선언
}
```

<br>

### `init` (초기화) 방법
인스턴스를 생성할 때 모든 프로퍼티를 초기화해야 하며, 이를 위해 `init` 키워드를 사용

<br>

#### `class`에서 `init`
- 모든 프로퍼티의 값을 할당하기
	
    - `값이 없을 수 있는 옵셔널 타입`, `초기값을 준 프로퍼티`는 예외
- `init`을 여러개 만들 수 있음
- `convenience init`(보조 초기화) 기능 제공 (struct에서는 제공하지 않음)

<br>

#### 초기화 방법

<br>

1️⃣ 지정 초기화
클래스에서 가장 핵심이 되는 초기화 함수
- 모든 프로퍼티를 제대로 채우고, 부모 클래스 것도 챙겨서 위로 연결


```
// 일반적인 init

class Person {
	var name: String // 값을 저장하는 저장 프로펕
    var age: Int
    
    init(name: String, age: Int) {
    	self.name = name
        self.age = age
    }
}

let person = Person(name: "Brody", age: 25)
```

<br>

**상속 있는 경우**
```
class Animal {
    var species: String
    init(species: String) {       // 부모 지정 초기화
        self.species = species
    }
}

class Dog: Animal {
    var name: String
    
    init(species: String, name: String) { // 자식 지정 초기화
        self.name = name                 // 내 프로퍼티 먼저 채우고
        super.init(species: species)     // 부모 초기화 호출
    }
}
```


<br>

2️⃣ 기본값 초기화
- 프로퍼티에 기본값을 넣으면 초기화를 진행하지 않아도 된다.

```
class Dog {
    var name: String = "멍멍이"  // 기본값
    var age: Int = 1            // 기본값
}

let d = Dog()   // init 없어도 됨
print(d.name)  // "멍멍이"
print(d.age)   // 1

```

<br>


```
class Person {
	var name: String = "이름없음"
    var age: Int = 0
}

let person = Person()

// 혹은 파라미터를 받지 않는 init에서 모든 프로퍼티 값을 정해줄 수 있음

class Person {
	var name: String
    var age: Int
    
    init() {
		self.name = "이름없음"
        self.age = 15
    }
}
```
- 만약 프로퍼티의 기본값이 하나라도 빠진다면 `init`을 구현하여 모든 값에 프로퍼티의 값을 채워주어야 한다.

<br>

3️⃣ 여러개의 `init` 사용
- 여러가지 방법으로 초기화

```
class Person {
	var name: String
    var age: Int
    
    init(name: String, age: Int) {
    	self.name = name
        self.age = age
    }
    
    init(name: String) {
    	self.name = name
        self.age = 0
    }
    
    init() {
    	self.name = "이름없음"
        self.age = 15
     }
 }
 ```
 
 <br>
 

 4️⃣ `covenience init`: 보조 초기화
 - 클래스에서만 사용 가능
 - `self.init`을 사용하여 초기화를 도와줌
 
```
 class Person {
 	var name: String
    var age: Int // 기본값 제공 X
    
    init(name: String, age: Int) {
    	self.name = name
        self.age = age
    }
    
    convenienve init(name: String) {
    	self.init(name: name, age: 0)
    }
}
let person = Person(name: "이름만 있어요!")
print(person.age) // 0
```


<br>

#### `deinit`: 소멸자
- class에서만 사용 가능
- 사용이 종료된 인스턴스가 메모리에서 해제될 때 자동 호출
- 직접 호출 불가

```
deinit {
	// 구현부
}
```

