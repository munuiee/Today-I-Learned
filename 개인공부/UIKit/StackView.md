## StackView 속성
1. Axis: 방향
2. Alignment: StackView의 서브뷰를 어떤식으로 정렬할지 결정 (Vertical, Horizontal)
3. distribution: 사이즈 분배 
4. spcing: 뷰 사이의 간격

<br>
<br>

# StackView❓
여러개의 뷰를 정렬해서 나타내는 인터페이스

## 종류
- Horizontal(수평)
- Vertical(수직)

<br>
<br>
<br>

### 💠 Horizontal StackView Alignment
1. Fill(디폴트): StackView에 서브뷰들을 빈공간 없이 채움 (+ 높이)
2. Top: 서브뷰들의 원래 크기를 유지하면서 StackView의 위에 붙여서 정렬
3. Center: 서브뷰들의 원래 크기를 유지하면서 StackView의 중앙에 정렬
4. Bottom: 서브뷰들의 원래 크기를 유지하면서 StackView의 하단에 붙여서 정렬
5. First Baseline: 첫 번째 기준선을 기준으로 정렬
6. Last Baseline: 마지막 기준선을 기준으로 정렬

<br>

Horizontal Stack View 안에 세 개의 Label을 넣어보았다. <br>
첫 번째 Label에 Height 100을 주고 Alignment 설정을 해보았어요 <br>
StackView는 내부 뷰의 크기에 따라 사이즈가 자동으로 정해지기 때문에 위치만 설정해주어도 AutoLayout 설정이 된다. <br>
<br><br>
#### 1️⃣ Fill
<img width="458" height="358" alt="스크린샷 2025-08-18 오후 2 23 10" src="https://github.com/user-attachments/assets/1f460e84-7b8a-4d60-bf6c-9000ff8137a9" />

<br><br>

#### 2️⃣ Top
<img width="458" height="358" alt="스크린샷 2025-08-18 오후 2 23 16" src="https://github.com/user-attachments/assets/cec51e14-4102-4301-baaf-df11cff82c25" />

<br><br>

#### 3️⃣ Center
<img width="458" height="358" alt="스크린샷 2025-08-18 오후 2 23 23" src="https://github.com/user-attachments/assets/b0ad37e8-e2f1-487c-8baa-1e358eff98a5" />

<br><br>

#### 4️⃣ Bottom
<img width="458" height="358" alt="스크린샷 2025-08-18 오후 2 23 28" src="https://github.com/user-attachments/assets/e985339d-1a20-48f1-8156-a78b60e988ef" />
<br><br><br>

### 💠 Vertical StackView Alignment
1. Fill: StackView의 너비에 맞춰 늘어나면서 정렬되며, 디폴트 값임
2. Leading: 서브뷰의 원래 길이를 유지하면서 StackView의 글자 시작 방향부터 정렬되어서 채워짐
3. Center: 서브뷰들의 Center가 StackView의 Center에 배치
4. Trailing: 서브뷰들의 원래 길이를 유지하면서 StackView의 글자가 끝나는 방향부터 정렬되어서 채워짐

<br>
위와 같은 조건으로 핑크색 레이블에 Width 100을 줬다.
<br>


#### 1️⃣ Fill
<img width="384" height="241" alt="스크린샷 2025-08-18 오후 3 49 52" src="https://github.com/user-attachments/assets/dee54cd9-ad10-4440-8a1c-9718d6f001c1" />

<br><br>

#### 2️⃣ Leading

<img width="384" height="241" alt="스크린샷 2025-08-18 오후 3 49 58" src="https://github.com/user-attachments/assets/b9e30ef3-2737-4ba9-8ac4-12ece9cffe6b" />

<br><br>

#### 3️⃣ Center
<img width="384" height="241" alt="스크린샷 2025-08-18 오후 3 50 13" src="https://github.com/user-attachments/assets/410fc8ac-8e9b-47c6-92bb-80405b5aa3d7" />

<br><br>

#### 4️⃣ Trailing
<img width="384" height="241" alt="스크린샷 2025-08-18 오후 3 50 19" src="https://github.com/user-attachments/assets/899af721-599f-493d-ac0c-247df310f7cc" />

<br><br><br>

### 💠 Distribution (Vertical과 동일)
: 스택뷰 안의 뷰들의 관계를 나타낼 때 사용
<br>

1. Fill Equally: StackView의 너비에 맞춰서 서브뷰들이 너비를 동일하게 맞춤
2. Fill Proportionally: StackView의 intrinsic content size에 맞춰서 너비 조절
3. Eqaul Spacing: 서브뷰 사이의 간격을 조절하여 StackView를 채움
- 서브뷰가 StackView보다 크다면 Compression Resistance Priority를 기준으로 감소
- 우선순위가 모두 동일하다면 인덱스 순서대로 변경
4. Equal centering: StackView 안 서브뷰들의 center를 구해서 각 서브뷰간의 center 거리가 동일하도록 조절

<br>

#### 1️⃣ Fill Equally
<img width="426" height="274" alt="스크린샷 2025-08-18 오후 3 56 07" src="https://github.com/user-attachments/assets/290c4aeb-2d54-4c71-ae91-83eae1066b98" />
<br> 모든 뷰의 크기를 같게 맞춰줌
<br><br>

#### 2️⃣ Fill Proportionally
<img width="426" height="274" alt="스크린샷 2025-08-18 오후 4 09 24" src="https://github.com/user-attachments/assets/ce49426f-cc4b-4b37-b022-a7b7c514a584" />
<br> 컨텐츠의 크기가 크면 여백이 커지고, 크기가 작으면 여백이 작아짐 <br>
회색이 제일 여백이 작은 이유

<br><br>

#### 3️⃣ Equal Spacing
<img width="426" height="274" alt="스크린샷 2025-08-18 오후 3 56 30" src="https://github.com/user-attachments/assets/4b50bbc7-51b9-4622-b866-6ce8e2ff0abc" />
<br> 모든 뷰의 간격을 동일하게

<br>

Spacing을 20으로 설정했더라도 이와 상관 없이 뷰들의 Spacing이 동일하게 지정됨 <br><br>
<img width="426" height="274" alt="스크린샷 2025-08-18 오후 4 01 47" src="https://github.com/user-attachments/assets/73540f5e-d84c-4e53-826e-2ad6566336ac" />
<br><br> 뷰들의 사이즈가 아무리 커져도 Spacing은 내가 지정한 20만을 유지 <br><br>

#### 4️⃣ Equal Centering
<img width="426" height="274" alt="스크린샷 2025-08-18 오후 4 02 17" src="https://github.com/user-attachments/assets/fd0cbed1-775e-44a9-8160-5bfbf7ae1e52" />
<br> 가운데를 기준으로 간격이 맞춰진짐

<br><br>
