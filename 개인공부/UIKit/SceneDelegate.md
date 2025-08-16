# SceneDelegate

## Scene
iOS 13 이후부터 등장<br>
Scene에는 UI 하나의 인스턴스를 나타내는 windows와 ViewControllers가 포함된다.<br>
또한 각 Scene에 해당하는 UIWindowSceneDelegate 객체를 가지고 있고, 이 객체는 UIKit와 앱 간의 상호 작용을 조정하는 데 사용한다.<br>
Scene들은 같은 메모리와 앱 프로세스 공간을 공유하면서 서로 동시에 실행된다.<br><br>

결과적으로, 하난의 앱을 여러 Scnee과 SceneDelegate 객체를 동시헤 활성화할 수 있다.<br><br>

## Scene Session
UISceneSession 객체는 Scene 고유의 런타임 인스턴스를 관리한다.<br>
사용자가 앱에 새로운 Scene을 추가하거나 프로그래밍적으로 Scene을 요청하면, 시스템은 그 Scene을 추적하는 Session 객체를 생성한다.<br>

### Session<br>
- 고유한 식별자
- Scene의 구성세사항(Configuration Details)<br>

UIKit는 Session 정보를 그 Scene 자체의 생애(Life Time)동안 유지하고 App Switcher에서 사용자가 그 Scene을 클로징하는 것에 대응하여 그 Session을 파괴한다.
Session 객체는 직접 생성하지 않고 UIKit가 앱의 사용자 인터페이스에 대응하여 생성한다.<br><br>

## SceneDelegate 메서드

`scene(_:willConnectTo:options:)`<br>
scene이 앱에 추가될 때 호출하는 메서드<br>
☝️ 단, 여기서 ViewController와 같은 클래스 객체를 만들어 사용할 때, 이 메서드에서 viewDidLoad()가 호출되지 않는다.<br><br>

`sceneDidDisconnect(_:)`<br>
scene의 연결이 해제될 때 호출되는 메서드<br>

`sceneDidBecomeActive(_:)`<br>
App Switcher에서 선택되는 등 scene과의 상호작용이 시작될 때 호출되는 메서드
<br>
💁🏻‍♀️ App Switcher: 홈 버튼을 두 번 누르거나 하단에서 위로 스와이프시 현재 실행 중인 앱들이 보이는 화면<br><br>

`sceneWillResignActive(_:)`<br>
사용자가 scene과의 상호작용을 중지할 때 호출되는 메서드 (다른 화면으로의 전환)<br><br>

`sceneWillEnterForeground(_:)`<br>
scene이 foreground로 진입할 때 호출되는 메서드<br><br>

`sceneDidBackground(_:)` <br>
scene이 background로 진입할 때 호출되는 메서드



