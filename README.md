# MVC-MVVM-patten


마기의 개발 블로그
즐겁게 개발을 하고 싶은 욕심 많은 개발자

Blog About Archive Tags
MVC, MVP, MVVM 비교
안녕하세요. 마기입니다. 개발 관련 블로그 정리 두번째 시간입니다.

이번 시간에는 협업, 유지보수, 테스트의 용이성 등을 위한

쾌적하고 좋은 환경에서 개발을 하기 위한 프레임워크 패턴들에 대해서 알아보겠습니다.

종류로는 웹 개발시 많이 쓰이는 MVC부터 시작해서 파생되어 나온 MVP, MVVM, Viper 등등

많은 패턴들이 있습니다.

이 많은 프레임워크 패턴들의 공통적인 특징이자 장점은 다음과 같습니다.

화면에 보여주는 로직과 실제 데이터가 처리 되는 로직을 분리

그냥 분리 하지 않고 잘 섞어서 처리를 해도 프로그램은 잘 돌아갑니다.

하지만 프로그램의 몸집이 점점 커진다면 어떻게 될까요..

예를 들어서 화면의 버튼을 누르면 서버에 데이터를 요청하고

요청한 데이터를 받은 다음.. 화면에 맞게 가공하고 정렬해서

실제 화면의 UI에 보여주게 되는 클래스가 있다고 합시다.

뭐.. 이정도 작업은 괜찮습니다.

그런데 다른 버튼을 눌러서 Local DB에서 값을 가져와서 가공한 후에 보여주고..

또 다른 버튼을 누르면 또 다른 작업을 추가로 해서 또 보여주고..

모듈화를 잘 시키면 그나마 낫겠지만 그것도 한계가 있을것입니다.

결국 코드가 뒤죽박죽 지저분해지고 뭐가 뭔지 모르게 되겠죠.
이럴거면 차라리 잘 정리해보자..

화면에 보여주는거 따로 실제 처리 되는거 따로 나누면 찾기도 쉽고 보기도 쉽지 않을까

그래서 나온것이 아래 설명할 프레임워크 패턴입니다.

이제 MVC, MVP, MVVM 패턴을 비교 정리해 보겠습니다.

(Viper는 ios에서 많이 쓰이는 패턴입니다. 차후에 정리하도록 하겠습니다.)

MVC (Model + View + Controller)
mvc 

MVC는 Model과 View, 그리고 Controller 세가지 요소로 구성 되어 있습니다.

Model : 프로그램에서 사용되는 실제 데이터 및 데이터 조작 로직을 처리하는 부분

Model은 프로그램에서 사용되는 실제 데이터이며 불러오거나 업데이트 하는

로직이 추가 되어 있습니다.

View : 사용자에게 제공되어 보여지는 UI 부분

View는 실제 사용자가 눈으로 보고 있는 화면 입니다.

웹이라면 웹페이지, 모바일 어플의 화면이 View에 해당한다고 보시면 됩니다.

Controller : 사용자의 입력을 받고 처리하는 부분

Controller는 사용자의 입력을 받은 다음 해당 작업을 처리 하는 부분 입니다.

정리를 하자면!

Controller로 사용자의 입력이 들어옵니다.
Controller는 Model을 데이터 업데이트 및 불러오고
Model은 해당 데이터를 보여줄 View를 선택해서 화면에 보여주게 됩니다.
MVC는 단점이 있습니다. View와 Model이 서로 의존적이라는 점입니다.

최대한 서로의 의존성을 줄일수 있도록 노력해야 합니다.

그런 노력에 의해 파생되어 나온 프레임워크가 다음으로 설명드릴 MVP 패턴 입니다.

MVP (Model + View + Presenter)
mvp

MVP는 Model과 View는 같습니다. 다만 Controller 대신 Presenter가 존재합니다.

Presenter : View에서 요청한 정보를 Model로 부터 가공해서 View로 전달하는 부분

Model과 View는 MVC와 동일하지만 사용자 입력을 View에서 받습니다.

그리고 Model과 View는 각각 Presenter와 상호 동작을 하게 됩니다.

항상 Presenter을 거쳐서 동작하는 것이죠.

그러므로 View와 Model은 서로를 알필요가 전혀 없습니다. Presenter만 알면 되죠.

그래서 MVC의 단점인 View와 Model의 의존성이 없어지게 됩니다.

정리를 하자면!!

View로 사용자의 입력이 들어옵니다.
View는 Presenter에 작업 요청을 합니다.
Presenter에서 필요한 데이터를 Model에 요청 합니다.
Model은 Presenter에 필요한 데이터를 응답 합니다.
Presenter는 View에 데이터를 응답 합니다.
View는 Presenter로부터 받은 데이터로 화면에 보여주게 됩니다.
이런 MVP도 단점이 있습니다. View와 Model은 의존성이 없는 대신

View와 Presenter가 1:1로 강한 의존성을 가지게 됩니다.

이런 단점을 해결할 또 다른 프레임워크가 등장을 합니다. 바로 MVVM 입니다.

MVVM (Model + View + ViewModel)
mvvm

MVVM은 WPF나 SilverLight에서 많이 사용되는 프레임워크 패턴 입니다.

역시 Model과 View는 다른 프레임워크 패턴과 같습니다.

하지만 이번에는 Presenter 대신 ViewModel이 존재 합니다.

ViewModel : View를 표현하기 위해 만들어진 View를 위한 Model

MVVM은 두가지 디자인 패턴을 사용합니다. 바로 Command패턴과 Data Binding 인데요.

이 두가지 패턴으로 인해 View와 ViewModel은 의존성이 완전히 사라지게 됩니다.

MVP와 마찬가지로 View에서 입력이 들어오구요. 입력이 들어오면 Command 패턴을 통해

ViewModel에 명령을 내리게 되고 Data Binding으로 인해 ViewModel의 값이 변화하면

바로 View의 정보가 바뀌어져 버리게 됩니다.

정리를 하자면!

View에 입력이 들어오면 Command 패턴으로 ViewModel에 명령을 합니다.
ViewModel은 필요한 데이터를 Model에 요청 합니다.
Model은 ViewModel에 필요한 데이터를 응답 합니다.
ViewModel은 응답 받은 데이터를 가공해서 저장 합니다.
View는 ViewModel과의 Data Binding으로 인해 자동으로 갱신 됩니다.
프레임워크 패턴에 대한 고찰
위와 같이 세가지 프레임워크 패턴을 비교하고 장점과 단점을 이야기 했지만

이 패턴은 무조건 좋아! 이건 쓰면 안될거 같아..

이런건 없습니다. 사실 뭐가 맞는지.. 뭐가 틀린지.. 정답은 없죠.

전부다 좋은 패턴 들입니다. 괜히 개발자들이 많이 쓰고 발전 시킨게 아니죠!

프로젝트의 크기와 여러 상황에 맞게 비교 검토 하시고 사용 하시면 됩니다.

그리고 다른 디자인 패턴들도 마찬가지이지만 프레임워크 패턴을 처음 적용 하시는 분들은

처음부터 완벽하게 파고 들어서 구현하시기보다는 조금씩 천천히 적용하시길 추천 드립니다.

급하게 힘들게 파고 들다가는 배보다 배꼽이 더 커지는 상황을 경험 하실 수도 있습니다.

마치며..
프레임워크 패턴들을 정리 했지만 잘못 이해한 부분이 있을수도 있습니다.

언제든지 피드백 주시면 반영후 수정 하겠습니다. 많은 피드백 부탁 드립니다.

다음 포스트부터는 당분간 안드로이드에서 제일 많이 사용되고 있다고 알려진

MVP 프레임워크를 구현해 볼 생각입니다.

빠른 분석을 위해 여러 외부 라이브러리 및 프로그래밍 기법들은

모두 배제할 생각 입니다. (rxJava, Dagger, 하다못해 Butter Knife 까지도..)

그럼 다음에 뵙겠습니다.

Written on February 24, 2017

Tagged:androidmv


 
