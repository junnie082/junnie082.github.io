---
layout: post
title: 피우다 앱 개발 프로젝트
subtitle: 플러터 앱 개발
author: Jun
categories: contest framework language
banner:
  video: #https://vjs.zencdn.net/v/oceans.mp4
  loop: true
  volume: 0 #0.8
  start_at: 8.5
  image: https://bit.ly/3xTmdUP
  opacity: 0.618
  background: "#000"
  height: "100vh"
  min_height: "38vh"
  heading_style: "font-size: 4.25em; font-weight: bold; text-decoration: underline"
  subheading_style: "color: gold"
tags: plans
sidebar: []
---

# 2023.06.13.(화)

6월 13일 드디어 피우다 프로젝트 끝.

본격적인 개발은 끝이 났다.

5월 10일부터 그 주 주말까지는 기획한 것을 토대로, 피그마를 사용하여 앱의 전체적인 도안을 모두 그렸다.

5월 14일에 노마드 코더 Dart 강의를 모두 보았다. 날밤을 까서 전부 봤는데.. 다 보는 데에 5~6 시간 정도 걸린 것 같다. 언어 자체가 어렵지는 않아서, 한 번씩 보고 따라쳐보니 쉽게 감이 왔다.

5월 15일에 회장님의 도움을 받아 맥북을 초기화 하고 homebrew 로 iTerm, VSC, 플러터를 깔고 세팅을 마쳤다.
이때 터미널을 많이 사용하게 되면서, Unix/리눅스/운영체제 공부를 따로 해야 할지 고민을 했는데, 용래 오빠가 운영체제 공부는 따로 하기보다는 여러 번 쓰면서 자연스럽게 손에 익히는 게 좋다고 하셨다. 지금 하고 있는 거에만 집중해도 충분할 거라고.

5월 16일에는 노마드 코더의 Flutter 로 웹툰 앱 만들기 강의를 보면서 클론 코딩을 했고, 이 강의는 다 보는 데 하루 정도 소요 되었다. 밤을 꼬박 새서 전부 들었고, 클론 코딩을 해보니 프론트 엔드는 쉽게 감이 왔다.

5월 17일에는 <마포장애인복지관> 웹사이트에서 웹스크래핑하여 공지사항 및 복지 관련 정보를 가져오는 것을 해보았는데, 이때 승훈이와 gpt 의 도움이 없었더라면 해내기가 어려웠을 것이다. await... async... 방학 동안에 백엔드 공부도 함께 하여야 겠다.

5월 18일에는 `지도` 기능을 만들기 시작했는데, 이때 구글 맵 API 를 가져오기로 했다. API Key 를 받으려면 돈을 내야 했으므로, 무료 버전으로 정말 딱 '지도' 만 가져왔다.

5월 19일까지 피그마를 보면서 전반적인 뼈대 (프론트 엔드) 를 완성시켰다(이때 gpt 의 힘을 다시 한 번 확인했다. 인간 코더는 이제 정말 필요 없을지도?).

5월 22일에는 어떤 오류가 계속 났는데, Kotlin Gradle Plugin Version 을 1.5.20 이상으로 설정하라는 에러 메세지가 떴다. 그런데 아무리 dependencies 에서 kotlin version 을 1.8.21 로 바꾸어 주었는데도 계속 같은 에러가 났다. 용래 오라버니께서 해결해 주셨는데, ./gradlew war --info 로 원인을 찾았다. cache 파일의 version 이 바뀌어 있지 않아서 생긴 문제였다. 이건 VSC 에 없는 파일이어서 아마 나 혼자서는 해결책을 찾지 못했을 것이다.

5월 23일부터 6월 1일까지는 시험 기간이었으므로 앱 개발을 진행하지 못했다. (정말 딱 하루씩 공부했는데... 객체지향프로그래밍 언어가 A+ 나왔다. 왜 나에게?)

5월 25일에 중간 미팅이 있었는데, 복지관 관계자님께 여러 가지 이야기를 들어볼 수 있는 아주 귀중한 시간이었다.
여기서 얻은 교훈. 꼭 다른 사람들의 이야기를 먼저 듣고, 필요가 있는, 즉 수요가 있는 서비스를 만들 것.

5월 31일에 웅진씽크빅 게임 개발 챌린지 (AI 쿼리도) 본선 진출 실패해서 멘탈이 나갈 뻔했지만 다시 멘탈을 되찾았다.

6월 8일에 거의 완성이 되었는데, 영진이가 연동 시켜놓은 firebase 때문인지 iOS 에뮬레이터에서 작동이 되지 않았다. iOS 개발자 등록이 안되어 있어서 발생한 문제인 것 같았다. 팀원들과 모여 하루 종일 삽질, 또 삽질.
XCode 에서 Runner 파일을 열어 설정을 해주었어야 했는데, 이 파일을 열려면 프로젝트 root 에서 open iOS/Runner.xcworkspace 명령어를 쳐주면 되었다.
태우가 또 40분 늦어서 화가 났지만... 그래도 그 자리에 앉아서 BMI 계산기 로직과 홈화면을 구현하고 가게 했다.

6월 9일, iOS 파이어베이스 문제에서 나는 팀원들에게 iOS 파이어베이스 연동은 포기하고, 프론트 엔드만 일단 구현해서 제출하자고 했으나 영진이는 iOS 를 포기하고 안드로이드 환경에서 작업하면 될 것이라고 했다. 안드로이드 환경에서 발생하는 에러는 본인이 해결해 보겠다고...
솔직히 말해서 제출 기한까지 얼마 남지 않은 상태였고, 못미더웠지만 영진이를 믿어보기로 했다. 그렇게 하루종일 기다렸는데, 그 날 저녁에 연락이 왔다. 성공했다고. 얼마나 기특하던지.
그 전 같았으면, 내 의견을 주장하기 급급해서 영진이가 로그인 기능을 구현하는 데에 성공하지 못했을 수도 있고 영진이의 자존심을 상하게 했을 수도 있지만, 영진이를 끝까지 믿어준 것은 내가 잘 한 것 같다.

6월 10일. develop 브랜치가 날아갔다. develop 브랜치를 develop-testing 에 합치려고 했는데 (깃헙에서 머지할 때, 방향이 분명히 develop 에서 develop-testing 으로 이동하는 것을 확인했는데) 확인해 보니, develop 브랜치와 develop-testing 브랜치가 동일해져 버려, develop 의 파이어베이스 연동 부분이 전부 날아갔다.

- 왜 develop 브랜치를 develop-testing 브랜치에 병합했는데, develop 브랜치도 바뀌었을까??
  결국 이것 때문에, 영진이를 붙잡고 (제출 기한 하루~이틀 전에) 밤을 새서 아침 8시까지 프론트엔드와 백엔드를 수작업으로 합치게 되었다...

6월 11일 제출날. 발표 자료를 제출 직전까지 만들었다. 태우에게 시연 영상을 촬영하도록 시켰지만, 결국 중간에 과외하러 가버려서...
발표 자료, 시연 영상, 전부 내가 만들었다.
영진이가 피드백을 잘해줘서 정말 고맙다. 자존심 상할 때도 분명히 있었지만, 명심할 것. 배우는 과정에서 자존심을 내세우면 안된다. 듣고 깎고 배워라.

기획, 디자인, 개발, 발표 자료... 를 모두 만들다 보니... 발표를 가장 잘할 수 있는 사람이 나였다. 그래서 발표도 준비했는데, 6월 12일에 가족끼리 에버랜드 여행이 있었기 때문에 에버랜드에 가서 계속 연락을 주고 받으면서 (팀원들에게 대본을 써달라고 했다) 발표를 준비했고, 다음날 아침 3번 정도 발표 연습을 했다.

6월 13일 아침에 보니 컴퓨터가 든 가방이 없었다. 아빠 차에서 가방을 가지고 오는 걸 까먹은 것이다. 나는 에버랜드에서 성남 할머니 집으로 가서 하룻밤 잔 후에 바로 발표가 있을 공덕 프롬트원으로 갈 생각이었는데 아침에 한바탕 난리가 났다. 결국 아침 6시에 아빠한테 전화했더니... 세종에서 차를 끌고 와 가방을 주고 갔다.
우리 아빠... 되게 멋있다. 화 한 번 내지 않고... 세종으로 돌아갔다.

![text](/assets/images/banners/2023-06-13/0513.png)
![text](/assets/images/banners/2023-06-13/0514.png)
![text](/assets/images/banners/2023-06-13/0515.png)
![text](/assets/images/banners/2023-06-13/0516.png)
![text](/assets/images/banners/2023-06-13/0517.png)
![text](/assets/images/banners/2023-06-13/0518.png)
![text](/assets/images/banners/2023-06-13/0519.png)
![text](/assets/images/banners/2023-06-13/0520.png)
![text](/assets/images/banners/2023-06-13/0521.png)
![text](/assets/images/banners/2023-06-13/0522.png)
![text](/assets/images/banners/2023-06-13/0523_1.png)
![text](/assets/images/banners/2023-06-13/0523_2.png)
![text](/assets/images/banners/2023-06-13/0524.png)
![text](/assets/images/banners/2023-06-13/0525_1.png)
![text](/assets/images/banners/2023-06-13/0525_2.png)
![text](/assets/images/banners/2023-06-13/0526.png)
![text](/assets/images/banners/2023-06-13/0527.png)
![text](/assets/images/banners/2023-06-13/0528.png)
![text](/assets/images/banners/2023-06-13/0529.png)
![text](/assets/images/banners/2023-06-13/0530.png)
![text](/assets/images/banners/2023-06-13/0601.png)
![text](/assets/images/banners/2023-06-13/0602.png)
![text](/assets/images/banners/2023-06-13/0603.png)
![text](/assets/images/banners/2023-06-13/0604.png)
![text](/assets/images/banners/2023-06-13/0605.png)
![text](/assets/images/banners/2023-06-13/0607.png)
![text](/assets/images/banners/2023-06-13/0608_1.png)
![text](/assets/images/banners/2023-06-13/0608_2.png)
![text](/assets/images/banners/2023-06-13/0609_1.png)
![text](/assets/images/banners/2023-06-13/0609_2.png)
![text](/assets/images/banners/2023-06-13/0609_3.png)
![text](/assets/images/banners/2023-06-13/0610_1.png)
![text](/assets/images/banners/2023-06-13/0610_2.png)
![text](/assets/images/banners/2023-06-13/0610_3.png)
![text](/assets/images/banners/2023-06-13/0610_4.png)
![text](/assets/images/banners/2023-06-13/0610_5.png)
![text](/assets/images/banners/2023-06-13/0610_6.png)
![text](/assets/images/banners/2023-06-13/0610_7.png)
![text](/assets/images/banners/2023-06-13/0610_8.png)
![text](/assets/images/banners/2023-06-13/0612_1.png)
![text](/assets/images/banners/2023-06-13/0612_2.png)
![text](/assets/images/banners/2023-06-13/0613.png)

6월 13일 드디어 발표.

발표한 것에 대한 피드백을 받았는데, 결국 `죽도 밥도 안되는 앱` 이라는 것이 결론이었다. 다른 사람들의 이야기를 전부 듣고 모든 기능을 넣으려고 하니까, 이 앱의 차별화된 점을 모르겠다는 것.
왜 굳이 이 앱을 써야 하나?
차라리 하나의 장애, 하나의 기능에만 집중하고, 나머지 기능들을 추가해 나갔다면 그것이 오히려 훨씬 좋았을 것.

아쉽다...

그래도 한 달 간 날밤을 열심히 새워서 만든 '완성'된 창작물이기에 후회는 없다. 기획부터 공모까지, 무언가 정말로 해보았다는 것이 내게 큰 의미로 다가 온다. 제대로된 앱 개발을 처음이지 않은가.

[Best-Friend 깃허브 링크](https://github.com/junnie082/Best_Friend)
발표 자료를 보고 싶다면, Best-Friend.pdf 를 확인해라.

즐거운 경험이었다. 공부 열심히하고, 프로가 될 수 있게 지금 당장 이것저것 무언가를 계속 시도해 보는 것을 멈추지 말 것.
