## Ionic
<img src='https://user-images.githubusercontent.com/80729831/169634424-8a6ecc82-a2d8-44d1-bc86-6ccaebea83a9.png'/>

- 하이브리드 어플리케이션을 쉽게 만들기위한 프레임워크
[앱개발 유형 비교(네이티브, 모바일, 모바일웹앱, 하이브리드, 크로스 플랫폼) ](https://www.notion.so/57a5a2e2921f4b4e823039924228b87b)
- AngularJs를 기반으로 만들어짐
- 하이브리드 앱을 개발하기에 최적화된 환경을 제공하고, ionic은 HTML5 API를 사용할 수 있는 컴포넌트들과 크로스 플랫폼 빌드가 가능한 Cordova 기반으로 구성된 하이브리드 앱 개발 프레임워크
- Ionic Framework는 인기가 높으며 앱 스토어에 있는 앱의 15% 이상을 차지
- **‘한번 작성하고 어디에서나 실행’**
표준 웹 기술을 사용하여 iOS, Android, Electron 및 웹 앱을 빌드하기 위한 플랫폼 간 UI 구성 요소 및 기본 API 기능을 제공
- 역사적으로 Ionic Framework는 기본 iOS 및 Android 빌드 및 런타임 기능을 제공하는 Cordova와 같은 프로젝트와 쌍을 이뤘지만, 대부분의 새로운 Ionic Framework 앱은 Capacitor를 사용합니다.

[Build Native and Progressive Web Apps with React and Ionic](https://ionicframework.com/react#components)



## capacitor

<img src='https://user-images.githubusercontent.com/80729831/169634456-f659788f-a9c2-4aab-a47c-cc69487ea3aa.png'/>


- **Capacitor**는 iOS, Android, 데스크톱 및 웹에서 작동하는 웹 앱을 쉽게 build 할 수 있도록 해주는 크로스 플랫폼 앱 런타임
- web-focused APIs를 제공
따라서 인기 있는 모든 웹 기술 및 라이브러리를 사용하여 Capacitor로 모바일 앱을 빌드한 다음 동일한 코드를 사용하여 웹과 데스크탑에 동일한 앱을 배포할 수 있습니다.
- 기존의 Cordova 플러그인과 호환
- Capacitor는 [만족도에서 두 번째로 높은 점수를 받은](https://2021.stateofjs.com/en-US/libraries/mobile-desktop) 2020년 JS 현황 설문조사에서 인기 있는 모바일 및 데스크탑 도구 중 모바일 개발 접근 방식에 대한 마지막 경험이 Cordova를 사용했다면, Capacitor가 크게 개선되었음을 알 수 있을 것입니다.
- Cordova 같은 경우 build 를 하기 위해 cordova plugin library를 사용하며 cordova.js 내에 안드로이드 SDK/IOS 를 사용하여 앱을 build 한다.
반면 capacitor는 android studio/Xcode 를 사용하여 직접한 후, device 나 emulator에서 테스트가 가능하고 build 한다.

### react-native vs ionic 성능비교

[https://ionicframework.com/blog/ionic-vs-react-native-performance-comparison/](https://ionicframework.com/blog/ionic-vs-react-native-performance-comparison/)

1. Boot Time(부팅시간) → 비슷
2. Smooth Scrolling(스크롤링) → 비슷
3. Native Transitions(화면 전환) → 네이티브가 더 좋지만 아이오닉도 가능은 하다
4. Platform-specific or Unified Styling(메뉴얼 및 css 관련) → 비슷
5. Code Execution
    - react native앱은 ‘네이티브로 컴파일된다’는 오해
    - ionic react 와 react native는 모두 사전 컴파일 되는 것이 아닌 런타임에 javascript를 실행한다.
    - 모바일 환경에서 JavaScript 코드는 WKWebView와 같은 웹 보기에서 실행할 때만 JIT 엔진에 액세스할 수 있다.
    이 말은 즉, 웹 환경인 ionic은 계속해서 JIT엔진이 실행되고 있고,
    javascriptCore나 Hermes를 사용하는 react native는 JIT엔진을 엑세스할 수 없다.
    - 여기서 성능 차이 발생, JIT 컴파일이 없으면 자바스크립트 실행이 느려지고, 에너지 소비가 많다.
6. CPU Consumption and Energy Impact :
    - react-native가 더많은 부담을 주고 있다
    - cpu 사용도 낮음

<img src='https://user-images.githubusercontent.com/80729831/169633944-ef2fff9a-f41a-41cf-af83-7eaeeccc00ac.png'/>

## Top 10 Hybrid Mobile App Frameworks in 2022

1. Flutter
2. React Native
3. Ionic

[https://www.websoptimization.com/blog/hybrid-mobile-app-frameworks/](https://www.websoptimization.com/blog/hybrid-mobile-app-frameworks/)

## 참조 repo

https://github.com/mlynch/nextjs-tailwind-ionic-capacitor-starter


## reference

[https://ionic.io/](https://ionic.io/)
[https://capacitorjs.com/](https://capacitorjs.com/)
[https://ionicframework.com/](https://ionicframework.com/)