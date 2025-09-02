## Xcode의 기능들
📎 [Xcode Release Notes](https://developer.apple.com/documentation/xcode-release-notes)
📎 [Xcodes](https://www.xcodes.app)

### Xcode?
애플 소프트웨어 개발을 위한 IDE.

- Xcode Release Notes: 새로운 버전이 출시되었을 때 버전에 대한 정보를 정리한 노트
- Xcodes: 다양한 Xcode 버전을 담는 프로그램


<br>

#### 프로젝트 생성
| 항목 | 설명 | 비고 |
|:----|:----|:----|
|Product Name | 생성할 프로젝트 이름 | ex) MyTestApp|
| Team | 애플 개발자 인증서 선택 | 인증서가 있어야 실제 기기로 테스트하거나 앱스토어에 배포 가능 |
| Organization Identifier | 조직 or 도메인 이름 입력 | 한 회사에서 여러 개의 앱을 낼 수 있음 |
| Bundle Identifier | 앱 고유 아이디 | `com.adam.MyTestApp` |
| Interface | User Interface 선택 
| Storage | Core Data 사용 여부
| Include Tests | 테스트 코드 작성 여부 | 내 코드를 테스트하기 위한 코드 |


<br>


### Navigator Area

순서대로 (cmd + 1~9)
cmd + 0은 네비게이터 열고 닫는 단축키
![](https://velog.velcdn.com/images/jihyee10/post/be5cff54-3dd6-4031-b255-ce99c1ac53da/image.png)


1️⃣**프로젝트 네비게이터**
- 프로젝트를 구성하는 디렉토리 구조 파악
- Swift 파일, 리소스(이미지, 컬러 등) 파일, 연결된 라이브러리 등을 확인 가능
- 디렉토리, 파일 생성

<br>

**2️⃣ 소스 컨트롤 네비게이터**
- 소스 파일 버전 관리용 네비게이터
- commit, commit history 등 Git의 기능들을 사용하도록 돕는다.
- Git Repository와 연결해야 사용할 수 있다.

<br>

3️⃣ **북마크**
- 파일에 북마크를 해두면 파일이 아주 많은 프로젝트에서 북마크 해둔 파일을 찾기 쉽다.

<br>

4️⃣ **검색 네비게이터**
- 프로젝트 전체에서 검색
- Find → Replace로 기능을 바꿀 수도 있다.

<br>

5️⃣ **이슈 네비게이터**
- 프로젝트 빌드 중 경고나 에러 같은 이슈들을 보여준다.
- 경고: 빌드는 성공하지만 고치길 권장하는 이슈
- 에러: 빌드 실패하는 이슈

<br>


6️⃣ **테스트 네비게이터**
- 테스트 코드를 작성한 경우 테스트를 수행할 때 사용
- 유닛 테스트, UI 테스트에 사용
	
    - 유닛 테스트: 앱의 단위 기능들을 테스트
    - UI 테스트: 앱의 UI가 의도한대로 잘 노출되는지에 대한 테스트
    
<br>

7️⃣ **디버그 네비게이터**
- 프로젝트 실행 중 실행 내용을 보여줌
- CPU,  Memory, Disk, Network, Thread 등의 현황

<br>

8️⃣ **브레이크 포인트 네비게이터**
- 디버그에서 사용할 브레이크 포인트를 관리
	 
    - 브레이크 포인트: 프로젝트 실행 중 멈출 지점들을 삽입
- 브레이크 포인트 전체 선택/해제/비활성화 등 가능

<br>

9️⃣ **리포트 네비게이터**
- 작업의 결과를 리포트
- 빌드 기록


<br>

### Inspector Area

![](https://velog.velcdn.com/images/jihyee10/post/678cfd4f-3461-4da8-b20b-8cc3af5789e9/image.png)

1️⃣ **파일 인스펙터** (cmd + opt + 1)
- 선택한 파일에 대한 정보
- 파일명 변경
<br>

![](https://velog.velcdn.com/images/jihyee10/post/5c0a76aa-7f45-4aee-8612-dd6b0ab71b27/image.png)

2️⃣ **히스토리 인스펙터** (cmd + opt + 2)
- 현재 파일에 대한 히스토리 열람
- 커밋한 사람, 메시지, 날짜, 포인트 

<br>

![](https://velog.velcdn.com/images/jihyee10/post/7eea47f8-5663-45d3-8565-f1dd5e008164/image.png)

3️⃣ **퀵 헬프 인스펙터**
- 선택된 대상의 문서 제공
- 코드에서 문서용 주석을 작성하면 생성 가능
- 문서용 주석: `///`
- 문서용 주석을 달고, Option 누른 채로 주석을 단 대상을 클릭하면 문서 제공

```swift 
/// AdamClass 입니다.
///
/// AdamClass는 이런 용도의 클래스입니다.
///
/// Example:
/// ```swift
/// let adam = AdamClass()
///```
///
/// -seealso: EveClass도 보세요.
class AdamClass {
    // 일반 주석
}
```

![](https://velog.velcdn.com/images/jihyee10/post/d88930ff-0e52-4dee-a1f7-c646512eb5ee/image.png)

<br>

![](https://velog.velcdn.com/images/jihyee10/post/14c7d0d4-8b42-4ec9-b93f-6c366f3dab4c/image.png)

4️⃣ **아이덴티티 인스펙터**
- 인터페이스 빌더(iOS 개발에 사용되는 시각적인 툴, 스토리보드 등)일 때 아이덴티티 인스펙터 제공.
- 객체의 아이덴티티를 관리
- StoryBoard ID 등 객체의 고유한 데이터를관리

<br>

![](https://velog.velcdn.com/images/jihyee10/post/f2e6d66d-30bf-40af-90b4-7b45cbd11b20/image.png)

5️⃣ **어트리뷰트 인스펙터**
- 인터페이스 빌더일 때 제공
- 선택된 객체의 속성 관리

<br>


![](https://velog.velcdn.com/images/jihyee10/post/db765d56-e79a-44ae-bdc9-1fbcf11ce975/image.png)

6️⃣ **사이즈 인스펙터**
- 인터페이스 빌더일 때 제공
- 선택된 객체의 크기, 배치를 관리

<br>

![](https://velog.velcdn.com/images/jihyee10/post/116442cb-cc2b-4152-a0fb-5d91a2666657/image.png)

7️⃣ **커넥션 인스펙터**
- 인터페이스 빌더일 때 제공
- 인터페이스 빌더와 소스 코드 간의 연결 관리

<br>


### Editor Area
- 코드를 작성하는 영역
- 코드 작성 뿐만 아니라 스토리보드, xib 등 인터페이스 빌더도 실행

<br>

#### 💫 TIPS
- 중괄호 안에서 `cmd + option + (화살표 ← or →)`를 클릭하면 코드를 접고 펼 수 있다.
- `cmd`를 누른 채로 프로토콜, 클래스, 함수 등을 클릭하면 정의부로 이동
- `ctrl + cmd + (화살표 ← or →)`를 하면 페이지 뒤로 가기, 앞으로 가기


<br>

### Debug Area
📎 [OSLog](https://developer.apple.com/documentation/os/oslog)
- 프로젝트를 실행하면서 디버깅을 돕는 영역

    - 왼쪽 영역: 사용되는 변수들에 대한 정보
    - 오른쪽 영역: 콘솔창. `print()`나 `log()` 출력
    - `cmd + shift + y
    
#### Debugging?
소프트웨어에서 발생하는 오류(bug)를 찾아내고 수정하는 과정.
- 프로그램이 예상대로 작동하지 않을 때 그 이유를 찾아내고 그 문제를 해결하는 작업

<br>

1️⃣ `print()`문으로 디버깅하기
```swift
// ViewController.swift 

import UIKit

class ViewController: UIViewController {
    
    override func viewDidLoad() {
        super.viewDidLoad()
        
        let randomNumber = getRandomNumber()
        print("randomNumber = \(randomNumber)")
    }
    
    // 0 부터 100 중 랜덤한 수를 리턴하는 함수
    func getRandomNumber() -> Int {
        return Int.random(in: 0...100)
    }
}
```

<br>

2️⃣ OSLog 로그 찍기
```swift
import UIKit
import OSLog

class ViewController: UIViewController {
    
    override func viewDidLoad() {
        super.viewDidLoad()

        os_log(.default, "(default) randomNumber = \(self.getRandomNumber())")
        os_log(.debug, "(debug) randomNumber = \(self.getRandomNumber())")
        os_log(.info, "(info) randomNumber = \(self.getRandomNumber())")
        os_log(.error, "(error) randomNumber = \(self.getRandomNumber())")
        os_log(.fault, "(fault) randomNumber = \(self.getRandomNumber())")
    }
    
    // 0 부터 100 중 랜덤한 수를 리턴하는 함수
    func getRandomNumber() -> Int {
        return Int.random(in: 0...100)
    }
}
```

<br>


### ToolBar
![](https://velog.velcdn.com/images/jihyee10/post/ddb970a4-2b1f-4440-a203-50a57b1d7913/image.png)

- 프로젝트 닫기
- 프로젝트 정지/실행
- 시뮬레이터 고르기
- Build configuration 세팅 (빌드 환경을 여러 개로 나눠 관리)

<br>


### 컴파일 & 빌드
#### 컴파일 (Complie)
어떤 언어의 코드 전체를 다른 언어로 바꿔주는 과정
- 컴퓨터가 이해하기 쉬운 바이너리 파일로 변환

#### 빌드 (Build)
소스 코드 파일을 실행 가능한 소프트웨어 산출물로 변환하는 과정
- 컴파일만 해서는 실행 가능한 결과가 나오지 않음
- 프로젝트에 포함한 리소스까지 모두 말아 실행 가능한 결과 도출


<br>

### 앱 생명주기
📎 [App LifeCycle](https://developer.apple.com/documentation/uikit/managing-your-app-s-life-cycle)

- Unattached (= Not Running)
앱을 실행 중이지 않은 상태

- Foreground Inactive
앱을 실행했지만 사용자로부터 이벤트를 받을 수 없는 상태
앱을 완전히 활성화하기 이전 단계

- Foreground Active
앱을 실행했고 사용자로부터 이벤트를 받을 수 있는 상태
가장 일반적인 앱을 사용하고 있는 상태

- Background
앱을 실행한 뒤 백그라운드로 넘어간 상태
홈버튼을 눌러 밖으로 나갔을 때의 상태
그래도 메모리에 올라가 있음
ex. 음악 재생

- Suspend
백그라운드 상태에서 앱이 특별한 작업을 필요로 하지 않을 경우 접어드는 상태
OS가 판단하여 Background  → Suspend 상태로 변환시킨다.

<br>


### AppDelegate
- 프로젝트를 생성하면 자동으로 생성되는 클래스
- 앱의 생명주기와 관련된 다양한 메서드 제공

<br>

ex)
1️⃣ `didFinishLaunchingWithOptions`
```swift
func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
    // Override point for customization after application launch.
    return true
}
```
앱이 실행할 준비를 마친 초기 상황에 실행됨
👉 앱을 실행한 극 초반에 세팅해야할 코드들을 작성

<br>

2️⃣ `didBecomeActive`
앱의 상태가 `inActive`에서 `Active`로 변하기 직전 실행됨
👉 앱이 `Active`한 상태가 되기 전에 작성하고 싶은 코드 작성
ex) 앱이 백그라운드에 갔다가 돌아올 때마다 화면에 보이는 정보를 업데이트하고 싶을 때


<br>

### SceneDeleagate
- 프로젝트를 생성하면 자동으로 생성되는 클래스
- Scene을 다루는 클래스
- 아이패드에서 가로 모드, 화면 분할을 하면 각 분할된 화면이 Scene을 의미


<br>

### 퍼스트 파티
iOS 개발은 애플이 주관, 애플이 제공하는 툴들
ex) UIKit, URLSession 등

<br>

### 서드 파티 (제3자)
제3자가 제공하는 툴
CocoaPods, SPM(Swift Package Manager), Carthage 등을 이용해서 서드파티 라이브러리를 가져옴

- SnapKit: UI를 편하게 짜도록 돕는 라이브러리
- Alamofire: URLSession을 편하게 사용하도록 돕는 라이브러리
- KingFisher: 이미지 로드를 편하게 하도록 돕는 라이브러리
- Swinject: DI 및 ServiceLocating을 편하게 하도록 돕는 라이브러리


<br>

### lldb
Low Level Debuger
디버그 영역 중 오른쪽 영역에 lldb를 사용해서 디버깅
브레이크 포인트와 함께 사용하기 좋다.

- `po`: print object. 객체에 대한 값 출력
- `cmd + K`: 디버그 창 청소
- `expression`: 변수 선언
- `expression let $x = 100`: x=100 선언
