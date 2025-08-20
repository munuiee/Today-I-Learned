# guard
조건이 안 맞을 때 빠져나오는 문법 (= 안전장치)
```
guard 조건 else {
	return / break / throw / continue
}
```

조건이 참이면 통과하고, 거짓이면 else 블록으로 들어감.

<br>

```
func checkAdult(age: Int) {
	if age < 18 {
    	print("성인이 아닙니다.")
    }
    print("성인입니다.")
}
```

⬇️ `guard`
```
func checkAdult(age: Int) {
	guard age >= 18 else {
    	print("성인이 아닙니다.")
        return 
    }
    print("성인입니다.")
}
```


<br>

#### 여러 조건 검사
```
func login(id: String?, password: String?) {
	guard let id = id else {
    	print("아이디 없음")
        return
    }
   guard let id password = password else {
   		print("비밀번호 없음")
        return
   }
    print("로그인 시도: \(id), \(password)")
}
```
👉 `nil` 체크할 때 많이 사용

<br>

### 특징
- 조건이 거짓일 때만 `else` 블록 실행
- `else` 블록 안에는 무조건 종료문(`return`, `break`, `throw` 등)이 있어야 함
- 보통 함수 초반부에 유효성 검사, 예외 처리시 사용
- 통과하면 자연스럽게 아래 코드 실행
