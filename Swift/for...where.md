Swift에서는 반복문에 조건을 바로 붙일 수 있다. <br>
반복하면서 조건문(If)를 따로 안 쓰고 반복문 옆에 `where`로 조건을 걸어주는 것.

<br>

#### if를 썼을 때
```swift
for i in 1...10 {
	if i % 2 != 0 {
    	print(i)
   }
}
```

<br>

#### where을 썼을 때
```swift
for i in 1...10 where i % 2 != 0 {
	print(i)
}
```


<br>

내가 연습한 코드
```swift
func sumOdd (number: Int) -> Int {
    var sum = 0
    for i in 1...number where i % 2 != 0 {
            sum += i
        }
    return sum
}

let result = sumOdd(number: 3)
print(result) // 4
```
