# 협업을 위한 Git

## Organization
일종의 단체 계정. 개인 계정의 `Repository`에서도 저장소를 만들고 다른 개발자를 초대해 협업할 수 있지만, `Organization`을 사용하면 좀 더 쉽게 `Repository`와 멤버를 관리할 수 있다.

## Organization 생성하기
1. 상단의 `+` 버튼을 누르고 New Organizaion 선택
![](https://velog.velcdn.com/images/jihyee10/post/f1d2f1f9-6730-4538-90d4-36238e62aace/image.png)


2. 무료 단체 계정 생성해주기
![](https://velog.velcdn.com/images/jihyee10/post/cf190d37-2511-4761-8198-45e01e5d73ce/image.png)

3. 개설할 Organization 이름과 단체 이메일 계정 및 Organizaion의 소유자(개인 또는 회사) 입력 후 Next 클릭
![](https://velog.velcdn.com/images/jihyee10/post/447cb342-9c96-4f37-897f-ecd0d8a3e426/image.png)

4. Organization에 초대할 사용자의 이메일을 입력하고, Complete setup 버튼 클릭. 또는 Skip this step 버튼으로 이 단계 건너뛰기 가능
![](https://velog.velcdn.com/images/jihyee10/post/5450f6b5-503b-4ee7-808a-a7c83fe2a43d/image.png)


<br>

## 프로젝트(Projects)
작업 현황과 진행도를 볼 수 있는 메뉴. 이슈, PR(Pull Request)들을 하나의 작업으로 구분해 그 작업의 진행사항을 확인 할 수 있다!



### 프로젝트 생성하기

#### 프로젝트 종류
![](https://velog.velcdn.com/images/jihyee10/post/9af4da5e-33ce-47c5-be98-a9c737c7cd3a/image.png)

1️⃣ Featured
- 프로젝트의 여러 뷰 중에서 메인으로 보여줄 뷰를 고정
- 관리자가 특정 뷰(중요한 보드나 로드맵)를 Featured로 설정하면 다른 사람이 프로젝트에 들어왔을 때 그 뷰가 먼저 보임
- 하이라이트, 즐겨찾기 같은 개념

2️⃣ Table
- 스프레드시트 형태로 아이템을 보여줌
- 행 하나가 이슈나 PR 같은 개별 아이템, 열에는 상태, 담당자, 마감일 같은 속성이 나옴
- 필터, 정렬, 열 추가 또는 삭제가 가능해서 데이터 관리나 세부 편집에 용이

3️⃣ Board
- 칸반보드 스타일
- 각 열은 보통 상태(To Do, In Progress, Done)나 커스텀 분류로 나눔
- 드래그 앤 드롭으로 아이템을 옮기면서 진행 상황 한눈에 확인 가능
	- `To Do`: 해야할 작업
	- `In Progress`: 진행 중인 작업
	- `Done`: 완료된 작업

4️⃣ Roadmap
- 타임라인 뷰
- 각 아이템이 기간에 맞춰 가로 막대 형태로 배치
- 장기 계획, 마일스톤, 일정 의존성 파악할 때 유용

<br>
<br>

1. 상단에서 Projects > New Project 클릭
![](https://velog.velcdn.com/images/jihyee10/post/948807a3-d344-485a-8a13-bb7944069a0e/image.png)

2. 나는 먼저 Board를 생성해주었다 !
![](https://velog.velcdn.com/images/jihyee10/post/6c11ef82-9e65-49ff-b728-b30db3c2fbee/image.png)
![보드 기본 화면](https://velog.velcdn.com/images/jihyee10/post/0384866d-1244-4cab-a6bc-cb656e969851/image.png)

3. 프로젝트 이름을 변경해주고 각 보드 아래의 `+ Add item`을 통해 이슈(Issue)를 생성해줄 수 있다.
![](https://velog.velcdn.com/images/jihyee10/post/877e1979-9ce6-4701-9470-5df3b4b5d613/image.png)

- Todo
새로 추가되는 모든 이슈가 해당 (해야할 것, 새로운 기능 추가 또는 수정 등)
새로 추가 되는 모든 PR 해당

- In Progress
작업이 진행중이라는 것을 의미
새로 열린 모든 PR이 해당
새로 열린 모든 이슈가 해당

- Done
이슈가 Close 됐을 때
Merge가 된 PR이 해당 

👉 자동화가 적용됨. 만약 새로운 이슈를 만들었다면 Todo에 해당되므로 이슈가 Todo로 이동함. 이슈가 Close되면 자동으로 Done으로 이동. 진행을 한눈에 보기 쉬움!


여기서 이슈란 뭘까?

<br>

## 이슈 (Issue)
버그 수정, 새로 추가될 기능, 개선해야하는 기능 등등
모든 활동 내역에 대해서 issue를 등록하고 그 이슈 기반으로 작업을 진행하면 효율적으로 프로젝트를 관리할 수 있다.

<br>

4. 이렇게 이슈가 등록되면 다른 보드에도 옮길 수 있고 옆의 점 세 개 버튼을 눌러 리포지토리와도 연결할 수 있다. 
![](https://velog.velcdn.com/images/jihyee10/post/50e0a55f-eb65-4b00-a887-eb0474e969e5/image.png)

5. 이슈 텍스트를 클릭하면 이슈 수정 창이 뜬다.
![](https://velog.velcdn.com/images/jihyee10/post/fc3eede9-0a1b-4f92-bed0-57bf3771434b/image.png)

💁🏻‍♀️ 터미널로 이슈 커밋하기
`git commit -m "issue번호"`
![](https://velog.velcdn.com/images/jihyee10/post/470411e1-19a4-4bc1-843d-d6dcbdd08bd7/image.png)
#3이 이슈번호!

<br>

### issue 주요 기능
- Assignees: 해당 작업의 담당자 (이슈 작업자)
- Labels: 해당 작업의 성격 (커스텀 가능)
![](https://velog.velcdn.com/images/jihyee10/post/7a234ab2-8b81-453a-9347-3a7e652d3b4e/image.png)


	깃허브에서 제공하는 기본 레이블
    - bug: 예기치 않은 문제 또는 의도하지 않은 동작(버그)
    - documentation: 문서를 개선하거나 추가할 필요가 있음
    - duplicate: 해당 이슈 또는 PR이 기존에 있음
    - enhancement: 새로운 기능 요청
    - good first issue: 새 기여자가 시작하기 좋은 작업
    - help wanted: 도움이 필요한 작업
    - invalid: 유효하지 않거나 잘못된 이슈/PR
    - question: 질문이나 정보 요청, 추가 정보 필요
    - wontfix: 문제나 PR 요청에서 작업이 계속되지 않음



- Project: 만들어둔 Projects를 선택
- Milestone: 프로젝트가 도달해야 하는 목표 지점 지정


<br>

6. 이슈 닫기는 Close issue를 눌러주면 된다
![](https://velog.velcdn.com/images/jihyee10/post/e87be757-c98c-47ee-abaa-8fac3e8e1ded/image.png)

![](https://velog.velcdn.com/images/jihyee10/post/82e197ea-1c9b-4fff-98eb-2ea1b6fcbcfd/image.png)

닫힌 이슈는 자동으로 Done으로 이동된다!

7. 이슈는 리포지토리에서도 생성 가능하다! 이번엔 마일스톤을 생성하기 위해 Milestones 버튼을 눌러준다.
![](https://velog.velcdn.com/images/jihyee10/post/8f18d0af-c6e1-4802-83c0-b9b8bde060d9/image.png)

8. 제목, 기간을 적어준다
![](https://velog.velcdn.com/images/jihyee10/post/9cdfadf8-e0f8-4d31-8dad-c8bd2c847604/image.png)

9. 마일스톤을 확인하기 위해 이슈 하나를 더 만들어보았다. 오른쪽의 마일스톤 설정에서 방금 생성된 마일스톤 클릭!
![](https://velog.velcdn.com/images/jihyee10/post/5c89d7bd-8a8b-4453-b487-54d1be4acc4d/image.png)
![](https://velog.velcdn.com/images/jihyee10/post/7070f963-2238-41a4-890a-23a2840b4377/image.png)
그럼 이렇게 진행상황이 옆에 뜬다 !

<br>


## Pull Request
작업한 코드 병합 요청
따로 PR 없이 병합할 수 있지만 보통은 PR을 통해 코드를 병합한다. 
🤷🏻‍♀️ 왜죠?
- 자연스러운 코드 리뷰를 위해: 팀원이 작성한 코드 검토
- 코드 충돌을 최소화하기 위해

외에도 push 권한이 없는 오픈 소스 프로젝트에 기여할 때도 Pull Request 사용!

<br>

## git Rollback
프로젝트 진행에 문제가 발생했을 때 문제 발생 전으로 되돌리기
- 문제 있는 코드를 커밋했을 때
- 특정 파일을 빼먹었을 때
- 작업했던 코드가 목적없이 진행되었을 때

### 3가지 방법
#### `git reset`
HEAD(현재 체크아웃된 브랜치의 가장 최신 커밋)의 포인터를 `커밋 해쉬 위치`로 변경하고 커밋 해쉬 이후 커밋들을 삭제

👉 3가지의 reset
- `soft`: 되돌아가기 전에 현재의 코드를 staged에 남겨놓음
- `mixed`: 되돌아가기 전에 현재의 코드를 로컬에 남겨놓음 (기본값)
- `hard`: 되돌아가기 전의 코드로 아예 되돌아감


#### `git checkout`
브랜치에서 다른 브랜치로 HEAD 이동
HEAD를 중간에 넣으면 detached HEAD state -> 최신 커밋 기록과 연결이 되지 않아 에러 발생


#### `git restore`
이전 커밋기록을 새로 커밋하여 최신 상태로 지정 (복원)
