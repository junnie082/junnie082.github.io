---
layout: post
title: 클래스 다이어그램
subtitle: Class Diagram
author: Jun
categories: Web
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
tags: Java
sidebar: []
---

# 2023.09.18.(월)

## [클래스 다이어그램에 대하여](https://infinitejava.tistory.com/61)

UML 다이어그램에는 Structure Diagram (정적, 구조 표현)과 Behavior Diagram (동적, 시퀀셜) 이 있는데 클래스 다이어그램은 `Structure Diagram` 에 속한다.

다른 사람들과의 의사소통 또는 설계를 논의하거나, 전체 시스템의 구조 및 클래스의 의존성 파악 및 유지보수를 위한 설계의 back-end 문서를 작성할 때 사용한다.

** 작성 시 주의 사항 **
명확한 이름을 부여하고, 간결하게 그려야 한다(Getter, Setter, Constructor는 생략 가능). UML을 작성하는 것이 개발비용보다 더 들어가는 경우도 있으므로 비용을 고려하여 작성 여부를 검토하는 것이 좋다.

## Class

Class 는 객체지향에서 사용되는 클래스를 표현하는 모델링 언어이다.

클래스 이름, 멤벼 변수, 메서드로 나누어 표현한다.

![클래스 다이어그램](/assets/images/banners/2023-09-18/classdiagram.png)

### 클래스 이름

클래스 이름은 네모 박스 안에 기입한다.

- 상자의 가운데에 위치해야 한다.
- 굵은 글씨체로 기입해야 한다.
- 첫번째 글자는 대문자로 기입해야 한다.

### 멤버변수 (Attributes)

클래스의 멤버변수는 UML에서 Property 라고 하는 개념의 한 종류다.

[visibility] property-name: property-type

`visibility`

- +: public
- -: private
- #: protected
- ~: package

### 메서드 (Operations)

클래스의 메서드는 UML에서 Operation 이라고 하는 개념의 한 종류다.

[visibility] operation-name(property1, property2, ...): return-type

리턴타입은 : 콜론 뒤에 작성한다.

![클래스 다이어그램2](/assets/images/banners/2023-09-18/classdiagram2.png)

## Relationship

UML에서 Relationship은 클래스의 관계를 표현하기 위한 모델링 언어이다.

|      이름      |                                                                   의미                                                                   |                                 표기법                                  |
| :------------: | :--------------------------------------------------------------------------------------------------------------------------------------: | :---------------------------------------------------------------------: |
| Generalization |                                                                 상속관계                                                                 | ![Generalization](/assets/images/banners/2023-09-18/relationship1.jpeg) |
|   Dependency   |                            지역변수로 사용하거나, 파라미터로 사용하는 등 멤버 변수로 갖지 않고 사용하는 관계                             |   ![Dependency](/assets/images/banners/2023-09-18/relationship2.jpeg)   |
|  Realization   |                                           Dependency의 한 종류이고, 인터페이스를 구현하는 관계                                           |  ![Realization](/assets/images/banners/2023-09-18/relationship3.jpeg)   |
|  Association   |                                            Dependency와 달리 멤버 변수로 가지고 사용하는 관계                                            |  ![Association](/assets/images/banners/2023-09-18/relationship4.jpeg)   |
|  Aggregation   |       Association의 한 종류이며 전체와 부분의 관계를 가지는 클래스에 적용된다. 멤버변수로 가지고 있지만, new를 직접하지 않는 관계        |  ![Aggregation](/assets/images/banners/2023-09-18/relationship5.jpeg)   |
|  Composition   | Association의 한 종류이며 전체와 부분의 관계를 가지는 클래스에 적용된다. 멤버변수로 가지고 있고, Aggregation과 달리 직접 new를 하는 관계 |  ![Composition](/assets/images/banners/2023-09-18/relationship6.jpeg)   |
|     Nested     |                                                            Inner Class의 관계                                                            |     ![Nested](/assets/images/banners/2023-09-18/relationship7.jpeg)     |

### Generalization

상속 관계의 클래스를 실선으로 연결하고 Super class 쪽에 빈 삼각형을 그린다.

### Dependency

`Dependency`는 의존관계이다. 단, 한 클래스가 다른 클래스를 멤버변수로 가지지 않고 지역변수, 파라미터 등 일시적으로 사용하는 경우에 성립되는 관계이다.

### Realization

Realization은 인터페이스와 구현 관계이다. 두 클래스를 점선으로 연결하고 인터페이스쪽에 화살표를 그린다.

### Association

Association은 한 클래스가 다른 클래스를 멤버변수로 가지는 경우다. 두 클래스를 실선으로 연결하고 사용 당하는 클래스쪽에 화살표를 그린다.

### Aggregation

Aggregation은 한 클래스가 전체의 역할을 하고 다른 클래스가 부분의 역할을 하는 전체-부분 관계일 때 사용되는 표현이다.
Aggregation은 전체 클래스가 부분 클래스를 new 하지 않고 외부에서 주입 받는다.

반면, Composition은 전체가 부분 클래스를 직접 new 하여 사용한다.

### Composition

Composition은 Aggregation과 거의 동일하고 다른점은 사용하는 클래스에서 직접 new를 해준다는 점이다.
정확히 말하면 부분 클래스의 생명주기를 관리하는 경우다.
