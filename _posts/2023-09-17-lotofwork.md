---
layout: post
title: GDSC 코어 커리큘럼 준비, 웹해킹 스터디 준비, Block It 프로젝트 마무리, 독서
subtitle: 왜이렇게 하는 게 많은지...
author: Jun
categories: Web security Game Book
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
tags: Java SpringBoot Unity C# book web-hacking
sidebar: []
---

# 2023.09.17.(일)

## 1. GDSC 커리큐럼 준비

Web 커리큘럼 3주차는 내가 준비하기로 했다.
저번주까지 컨트롤러, 엔티티, JPA 에 관한 공부를 했더라면, 이번주차는 템플릿에 관한 얘기를 할 터이다.

![도메인](/assets/images/banners/2023-09-17/domain.png)

### 도메인이란?

도메인은, "질문", "답변", "사용자" 처럼 굵직한 요구사항 또는 문제 영역을 대표하는 말이다.  
각 도메인 별로 일단 패키지를 만들어 클래스들을 나누어 놓자.

![404에러](/assets/images/banners/2023-09-17/404error.png)

`http://localhost:8080/question/list` 에 접속해 보자.
404 에러가 발생한 것을 알 수 있다.

404 에러란, 사용자가 사이트에서 존재하지 않는 URL을 탐색했을 때 발생한다.  
`/question/list` URL에 대한 매핑이 있는 컨트롤러가 필요하다.

### @ResponseBody 어노테이션이란?

![@ResponseBody](/assets/images/banners/2023-09-17/responsebody.png)

클라이언트에서 서버로 통신하는 메세지를 요청(request) 메세지 라고 하며, 서버에서 클라이언트로 통신하는 메세지를 응답(response) 메세지라고 한다.

비동기통신을 하기 위해서는 클라이언트에서 서버로 요청 메세지를 보낼 때나 서버에서 클라이언트로 응답을 보낼 때 본문에 데이터를 담아서 보내야 하는데, 이 본문을 body 라고 한다.

요청 본문 requestBody, 응답 본문 responseBody 를 담아서 보내야 한다.

![@ResponseBody2](/assets/images/banners/2023-09-17/responsebody2.png)

@ResponseBody 어노테이션이 붙은 파라미터에는 http 요청의 본문 (body) 이 그대로 전달된다.  
HTTP 요청의 바디 내용을 통째로 자바객체로 변환해서 매핑된 메소드 파라미터로 전달해 준다.

@ResponseBody 자바객체를 HTTP 요청의 바디 내용으로 매핑하여 클라이언트로 전송한다.  
즉, @ResponseBody 어노테이션을 사용하면 http 요청 body 를 자바 객체로 전달 받을 수 있다.

### 템플릿

![template](/assets/images/banners/2023-09-17/template.png)

`템플릿`은 자바 코드를 삽입할 수 있는 HTML 형식의 파일이다.  
타임리프 (Thymeleaf) 템플릿 엔진을 사용하려면 설치가 필요하다.

![template](/assets/images/banners/2023-09-17/template2.png)

static 패키지에 question_list.html 을 만들고, 이 파일의 이름을 컨트롤러에서 리턴하면 question_list 코드가 화면에 반영된다.

![template](/assets/images/banners/2023-09-17/template3.png)

롬복의 주된 역할은 `@Getter`, `@Setter`가 자동으로 Getter, Setter 를 만들어 준다는 데에 있다. 마찬가지로 @RequiredArgsConstructor 또한 롬복이 제공하는 애너테이션으로, final 이 붙은 속성을 포함하는 생성자를 자동으로 생성하는 역할을 한다.

따라서 스프링 의존성 주입 규칙에 의해 questionRepository 객체가 자동으로 주입된다.

### 의존성 주입

![Dependency Injection](/assets/images/banners/2023-09-17/di.png)

의존성을 주입하는 3가지 방식.

1. `@Autowired` 속성 - 속성에 @Autowired 애너테이션을 적용하여 객체를 주입하는 방식
2. 생성자 - 생성자를 작성하여 객체를 주입하는 방식 (권장하는 방식)
3. Setter - Setter 메서드를 작성하여 객체를 주입하는 방식 (메서드에 @Autowired 애너테이션 적용이 필요하다)

`Model 객체`는 자바 클래스와 템플릿 간의 연결고리 역할을 한다. Model 객체에 값을 담아두면 템플릿에서 그 값을 사용할 수 있다.
Model 객체는 따로 생성할 필요 없이 컨트롤러 메서드의 매개변수로 지정하기만 하면 스프링부트가 자동으로 Model 객체를 생성한다.

### 타임리프 (Thymeleaf)

![Thymeleaf](/assets/images/banners/2023-09-17/thymeleaf.png)

`th:`로 시작하는 속성은 타임리프 템플릿 엔진이 사용하는 속성이다. 이 부분이 자바 코드와 연결된다.

![Thymeleaf](/assets/images/banners/2023-09-17/thymeleaf2.png)

타임리프의 속성

1. 분기분 속성  
   `th:if="${question!=null"}`
2. 반복문 속성  
   `th:each="question: ${questionList}"`
3. 텍스트 속성  
   `th:text="${question.subject}"`

### ROOT URL

![rooturl](/assets/images/banners/2023-09-17/rooturl.png)

`http://localhost:8080` 처럼 도메인명과 포트 뒤에 아무것도 붙이지 않은 URL 을 말한다.

```Java
@GetMapping("/")
public String root() {
    return "redirect:/question/list";
}
```

- redirect:<URL> - URL로 리다이렉트 (리다이렉트는 완전히 새로운 URL로 요청이 된다)
- forward:<URL> - URL로 포워드 (포워드는 기존 요청 값들이 유지된 상태로 URL이 전환된다)

### 서비스 (Service)

![Service](/assets/images/banners/2023-09-17/service.png)

스프링에서 데이터 처리를 위해 작성하는 클래스이다.  
대부분의 규모 있는 스프링부트 프로젝트에서는 리포지터리를 직접 호출하지 않고 중간에 서비스 (Service) 를 두어 데이터를 처리한다.

서비스가 필요한 이유는 무엇일까?

1. 모듈화  
   어떤 컨트롤러가 여러 개의 리포지터리를 사용하여 데이터를 조회한 후 가공하여 리턴한다고 하자. 이 기능을 서비스로 만들어 두면 컨트롤러에서는 해당 서비스를 호출하여 사용하면 된다.  
   서비스가 없다면 해당 기능을 필요로 하는 모든 컨트롤러가 동일한 기능을 중복으로 구현해야 한다.

2. 보안  
   컨트롤러가 리포지터리 없이 서비스를 통해서만 데이터베이스에 접근하도록 구현하는 것이 보안상 안전하다. 이렇게 하면 어떤 해커가 해킹을 통해 컨트롤러를 제어할 수 있게 되더라도 리포지터리에 직접 접근할 수는 없게 된다.

3. 엔티티 객체와 DTO 객체의 변환  
   엔티티 클래스는 데이터베이스와 직접 맞닿아 있는 클래스이기 때문에 컨트롤러나 타임리프 같은 템플릿 엔진에 전달하여 사용하는 것은 좋지 않다.  
   엔티티를 직접 사용하여 속성을 변경한다면 테이블 컬럼이 변경되어 엉망이 될 수도 있기 때문이다.

따라서, 엔티티 대신 사용할 DTO(Data Transfer Object) 클래스가 필요하다.  
서비스는 컨트롤러와 리포지터리의 중간자적인 입장에서 엔티티 객체와 DTO 객체를 서로 변환하여 양방향에 전달하는 역할을 한다.

![Service](/assets/images/banners/2023-09-17/service2.png)

![Service](/assets/images/banners/2023-09-17/service3.png)

리포지터리를 직접 사용하지 않고 Controller -> Service -> Repository 구조로 데이터를 처리할 것이다.

### 질문 상세 추가하기

![link](/assets/images/banners/2023-09-17/link.png)

`th:href` 에서 URL 주소를 나타낼 때에는 반드시 `@{` 문자와 `}` 문자 사이에 입력해야 한다.

![link](/assets/images/banners/2023-09-17/link2.png)

`@PathVariable` 에서 변하는 id 를 얻을 때에는 `@PathVariable` 애너테이션을 사용해야 한다.

이때, `@GetMapping(value="/question/detail/{id}")` 에서 사용한 id 와 `@PathVariable("id")`의 매개변수 이름이 같아야 한다.

### URL 프리픽스 (prefix)

![prefix](/assets/images/banners/2023-09-17/prefix.png)

list 메서드의 URL 매핑은 /list 이지만 클래스에 /question 이라는 URL 매핑이 있기 때문에 /question + /list 가 되어 최종적인 URL 매핑은 `/question/list` 가 된다.

## 2. 웹 해킹 스터디 준비

바쁜데... 결국 내가 스터디장이 되었다.  
깃허브도 관리하고, 회의도 이끌어 나가야 하고. 무엇보다도 성실하게 매주 주어지는 과제를 해내어야만 한다.

![webhacking](/assets/images/banners/2023-09-17/webhacking.png)

## 3. Block It 슬슬 마무리

프로젝트의 리드미 파일과 클래스 다이어그램 및 FSM 을 작성해야할 때가 왔다.

![classdiagram](/assets/images/banners/2023-09-17/classdiagram.png)
![fsm](/assets/images/banners/2023-09-17/fsm.png)
![readme](/assets/images/banners/2023-09-17/readme.png)

초안은 이렇게 작성하고, 내일 클래스 다이어그램, fsm 이 무엇인지 조금 더 공부한 후에 수정할 것이다.  
리드미도 내일 회의를 통해서 필요한 사진들과 (다른 팀원이 코드를 작성해 주어야만 프로그램을 돌려 사진을 찍을 수가 있다) 수정해야할 사항들을 얻을 것이다.

## 4. 독서

헬스 클럽의 `패배의 신호` 라는 책도 읽어서 독후감까지 썼다.

![book1](/assets/images/banners/2023-09-17/book1.png)
![book2](/assets/images/banners/2023-09-17/book2.png)
![book3](/assets/images/banners/2023-09-17/book3.png)

재밌구만!
