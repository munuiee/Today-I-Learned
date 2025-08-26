# ARC
Automatic Reference Couning
`Reference Type`의 인스턴스 메모리 관리를 자동으로 해주는 기능 (`Value Type`의 인스턴스는 `ARC`가 관리하지 않음)
- 메모리 관리를 직접 하지 않아도 `ARC`가 자동으로 메모리 관리를 처리
	
    - 인스턴스가 더이상 필요하지 않을 때 메모리에서 자동으로 해제됨
- `Reference Type`의 인스턴스를 참조할 때, 참조카운트가 증가하며, 이를 `strong` 참조라고 한다. (`default`)

- 참조카운트의 증가를 원하지 않는 경우 `weak` 또는 `unowned` 참조를 사용할 수 있다.

<br>

## ARC 동작 방식
#### 1. 인스턴스 생성과 메모리 할당
- `class`의 새로운 인스턴스를 생성할 때마다 ARC는 해당 인스턴스에 대한 정보를 저장할 메모리 공간을 할당한다.
- 이 공간에는 인스턴스의 **타입 정보와 프로퍼티의 값이 저장**된다.

#### 2. 참조 카운트 관리
ARC는 사용 중인 인스턴스가 메모리에서 해제되지 않도록 몇 개의 프로퍼티, 상수, 변수가 인스턴스를 참조하고 있는지 추적한다.
- 참조 시작 시: 카운팅 +1
- 참조 종료 시: 카운팅 -1
- 최종적으로 참조카운트가 0이 되면 인스턴스는 메모리에서 해제된다.

#### 3. 메모리 해제
참조 카운트가 0이 된 인스턴스는 더이상 필요하지 않기 때문에, ARC가 해당 인스턴스가 사용했던 메모리를 해제한다.
- 만약 참조 카운트가 0이 되기 전에 인스턴스가 해제되면, 이후 그 인스턴스에 접근하게 될 경우 앱 크래시가 발생할 수 있다.

<br>

## ARC 동작 시기
`컴파일타임`에 인스턴스의 참조 카운트를 증가 또는 감소시키는 코드를 자동으로 삽입

<br>

## Memory Leak
= `메모리 누수`

- 사용이 끝난 인스턴스가 메모리에서 해제되지 않고 남아있는 현상
- 메모리 공간이 불필요하게 사용되면 성능 저하가 발생할 수 있음

<br>

## 강한 순환 참조 Strong Reference Cycle
iOS에서 자주 발생하는 `Memory Leak`의 원인 중 하나.
```swift
class Person {	
	let name: String
    init(name: String) { self.name = name }
    var apartment: Apartment?
    deinit { print("\(name) is being deinitalized") }
}

class Apartment {
	let unit: String
    init(unit: String_ { self.unit = unit }
    var tenant: Person?
    deinit { print("Apartment \(unit) is being deinitialized") }
}
```

`Person`과 `Apartment`는 서로를 참조하고 있기 때문에 순환 참조가 발생할 수 있다.

<br>

```swift
var john: Person?
var unit4A: Apartment?

john = Person(name: "John") // RC : 1
unit4A = Apartment(unit: "4A") // RC : 1
```
두 인스턴스를 생성하고 각각 강한 참조로 참조하고 있는 상태 (Default가 Strong이기 때문에)

<br>

```swift
john!.apartment = unit4A // john의 아파트에는 unit4A를 할당해서 RC가 1 올라서 2가 됨
unit4A!.tenant = john // unit4A의 거주지에는 john을 할당해서 RC가 1 올라서 2가 됨
```
Person 인스턴스와 Apartment 인스턴스가 서로 강한 참조로 사용

<br>

```swift
john = nil // 참조가 종료되었으므로 Person instance RC에 -1
unit4A = nil // 참조가 종료되었으므로 Apartment instance RC에 -1
```
Person instance와 Apartment instance의 RC가 1로 사용이 종료되었지만 메모리에서 해제되지 않음.
- 강한 참조로 서로를 참조한다고 해서 **강한순환참조**라고 한다.


### 강한 순환 참조 해결방법
- 참조 카운트를 올리지 않으면 된다
- 참조 카운트를 올리지 않기 위해서는 `strong`이 아닌 `weak`, `unowned`를 사용하기

```swift
class Person {	
	let name: String
    init(name: String) { self.name = name }
    weak var apartment: Apartment?
    deinit { print("\(name) is being detinitialized") }
}

class Apartment {
	let unit: String
    init(unit: String) { self.unit = unit }
    weak var tenant: Person?
    deinit { print("Apartment \(unit) is being deinitialized") }
}

var brody: person?
var unit100A: Apartment?

brody = Person(name: "brody") // Person instance RC : 1
unit100A = Apartment(unit: "100평 아파트") // Apartment instance RC : 1

brody.apartment = unit100A // Person의 apartment가 weak 이기 때문에 RC가 올라가지 않음 RC : 1
unit100A.tenant = brody // Apartment의 tenant가 weak이기 때문에 RC가 올라가지 않음 RC : 1

brody = nil // Person instance RC 1 감소 -> RC : 0
unit100A = nil // Apartment instance RC에 1 감소 -> RC : 0
// RC가 0이 되어서 Person instance 메모리에서 해제, Apartment instance 메모리에서 해제

```

<br>

## 객체를 참조하는 방법 3
#### Strong
- 강한 참조
- `default`
- 객체를 참조 시작하면 참조카운트가 1 증가
- 객체 참조가 종료되면 참조카운트가 1 감소

#### weak

- 약한 참조
- 객체를 참조하면 참조카운트가 변하지 않음
- 객체 참조가 종료되어도 참조카운트가 변하지 않음
- `nil` 허용

#### unowned
- 미소유 참조
- 객체를 참조하면 참조카운트가 변하지 않음
- 객체 참조가 종료되어도 참조카운트가 변하지 않음
- `nil`이면 크래시 발생
