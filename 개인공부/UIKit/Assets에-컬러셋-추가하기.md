# Assets에 hex color 추가하기

## 1. Assets 열고 New Color Set 추가하기
<img width="623" height="336" alt="스크린샷 2025-08-17 오후 2 05 33" src="https://github.com/user-attachments/assets/db6403a4-9076-4efc-b7b8-df52594c13f7" />

<br>

## 2.
<img width="625" height="204" alt="스크린샷 2025-08-17 오후 2 08 04" src="https://github.com/user-attachments/assets/11de4cde-e612-47eb-b9c2-1ae733da7382" />
<br>
Any Appearance, Dark 두 개가 뜨는데, Dark 색상을 따로 지정할 경우, 라이트모드에서 보이는 해당 색깔 영역이 지정한 색으로 보인다. <br>
다크모드가 따로 디자인 되어있다면 해당 부분을 참고하여 컬리칩을 지정하는 것이 좋다.

<br>

## 3. 다크모드를 따로 만들지 않는다면 Shift키로 동시 선택 후 색상 지정하기
<img width="389" height="179" alt="스크린샷 2025-08-17 오후 2 15 35" src="https://github.com/user-attachments/assets/b352ff4b-cebc-4193-8ea5-5f9dc0d19268" />

<br>

## 4. 색상 등록
<img width="260" height="156" alt="스크린샷 2025-08-17 오후 2 16 18" src="https://github.com/user-attachments/assets/2f2ba365-2c30-4975-9078-fec60c614a6f" />

<br>
<br>

- 8-bit (0 ~ 255): 각 RGB 값을 0 ~ 255값 내외로 지정하는 방식
- 8-bit Hexadecimal: 16진수 형태의 색상 표기법

<br>
나는 Hex로 등록해야해서 8-bit Hexadecimal로 선택!
<br>

<br>
<img width="479" height="376" alt="스크린샷 2025-08-17 오후 2 18 13" src="https://github.com/user-attachments/assets/4a8e4025-ee09-466b-a3ec-ed7ba38bfd65" />
<br>
밑에 Show Color Panel로 색상표 확인 가능

<br>

## 5. 색상 적용하기
<img width="363" height="216" alt="스크린샷 2025-08-17 오후 2 20 25" src="https://github.com/user-attachments/assets/135472ba-0484-4f7f-b136-5505ba52333a" />
<br>
스토리보드 백그라운드 컬러에서 적용 가능하다.

<br>

### 코드 영역에서 적용하기
`self.myButton.backgroundColor = UIColor(named: Color)`
<br>
`self.myButton.backgroundColor = .Color`



