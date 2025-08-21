# 인스턴스 (Instance)
`class`, `struct`, `enum`과 같은 설계도를 기반으로 실제 메모리에 생성되는 실체 <br>
**`class`, `struct`, `enum`은 설계도**의 역할을 하고, **인스턴스는 설계도를 보고 직접 만들어서 메모리에 저장되어 있는 값**이다. 

<br>

## 객체
인스턴스의 다른 말
인스턴스가 생성된 후 클래스에서 제공하는 프로퍼티나 메서드를 사용할 때 주로 사용

<br>

## 프로퍼티 (Property)
`class`, `struct`, `enum`과 관련되어 있는 정보 또는 값

<br>

## 메서드 (Method)
`class`, `struct`, `enum`과 관련된 함수

<br>

## `init`
인스턴스를 생성할 때 상태를 초기화하여 생성해야 한다. <br>
인스턴스를 만들 때 사용되는 변수, 상수(프로퍼티)의 값을 정해주어야 한다.

- 프로퍼티를 넣어서 초기화하여 생성한다.
- `init` 키워드를 사용하여 모든 변수, 상수를 초기화 해야 한다.
- 변수나 상수에 기본값을 정해주거나 값이 없음을 나타내는 Optional 타입으로 선언하면 초기화하지 않아도 된다.

```
enum Season: String {
	case spring
    case summer
    case autumn
    case winter
}

let season: Season = .spring

```
👉 깂을 할당하면 자동으로 초기화 됨
