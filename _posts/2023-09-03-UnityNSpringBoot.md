---
layout: post
title: 유니티 활용법과 스프링부트 공부
subtitle: 본격 백엔드 공부 시작
author: Jun
categories: Web Game
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
tags: Java SpringBoot Unity C#
sidebar: []
---

# 2023.09.03.(일)

## Block It 유니티 프로젝트

기획, 인게임 로직 구현. 방학 동안 잘 끝내 두었다. 이제 정말 유니티를 써서 화면도 만들어 보고 할일들을 조금씩 해 나가야 하는데, 마침 개발 팀장님이 버튼은 어떻게 만드는지, 스크립트 코드는 어떻게 넣는지 방법을 알려 주셨다.

![UnityScene](/assets/images/banners/2023-09-03/UnityScene.png)

먼저 필요한 화면에 대한 패널을 만든다.
그 후에 버튼, 인풋필드, 텍스트 등등 필요한 UI 들을 가져다가 놓는다. 여기서 각 UI 들의 크기나 비율을 잘 맞추어야 한다. 전의 패널들과 직접 비교할 수도 있다.  
바로 C# 스크립트를 만들어 변수들을 선언하고, 각 변수들에 대응되는 객체들을 연결 시킨다.

![UnityCode](/assets/images/banners/2023-09-03/UnityCode.png)

만약 변수를 public 으로 선언한다면 UI 와 변수를 Unity 에서 그냥 연결 시키기만 하면 된다. 하지만 private 으로 선언하면 바로 연결 시킬 수가 없다.
private 으로 선언하였음에도 코드와 UI 를 연결 시키고 싶다면 `[SerializedField]` 를 옆에 붙여 주어야 한다.

패널들은 GameObject 로 선언해주고, SetActive 를 통해서 각 화면의 이동을 조절한다.
버튼은 onClick 이나 AddListener 를 통해 조작할 수 있다.

Unity 는 정말 많은 것들을 알아야 할 수 있을 것 같았다. 프론트엔드, 백엔드, 기획, 등등 모든 분야를 총망라하는 느낌이었다.

여하튼 개발 팀장님의 도움으로 이번주에 내가 맡은 일은 할 수 있었다.

## 스프링부트 Spring Boot

올해가 다가기 전에, 백엔드를 열심히 파보려고 한다.
그동안 파이썬이나 유니티를 써서 게임이나 키오스크 화면 등도 만들어 보고, 플러터와 다트를 써서 앱도 만들어 보고, 엉망진창 여러 가지를 찍어 먹어 보는 활동을 많이 했었다.
그런데 여러 가지 활동을 막 하다보면 해당 분야에 대한 이해가 깊어지기가 힘들다. 그동안은 내가 어느 분야에 관심이 있을지를 가늠해 보는 것이 주된 활동이었다면, 이제는 한 분야에 대한 공부를 깊이 해보는 것이 중요할 것 같다.
그래서 졸업 전에 한 가지 프레임워크나 언어에 대해서, '난 이 분야에 대해서만큼은 정말 잘 알아!' 라고 할 수 있을 정도로 자신감을 키워내는 것을 목표로 하고자 한다. 내가 선택한 분야는 백엔드이다.
프론트엔드도 재미있고, 인공지능도 흥미롭지만
백엔드 마스터가 되면 나~중에 정보 보안 쪽으로도 공부해 볼 수 있을 것 같다는 것이 이유다. 어느 분야든, 마스터가 되고 나면 다른 분야로 시야를 돌리는 데에는 큰 문제가 되지 않을 것 같아서 일단 백엔드를 열심히 파보려고 한다.

일부러 GDSC 동아리에서 Core 를 맡은 것도 있다. 아는 것이 정말 많이 없지만, Core 로써 다른 Member 들보다 책임감이 생기면, 강제로라도 더 열심히 공부하게 될 테니까.

저번주에 `점프투스프링부트` 온라인 교재를 한번 훑어 보았다. 이번주부터는 다시 해당 교재를 복습하고 있다.
저번주에는 STS (Eclipse) 를 써서 실습을 해보았지만, 이번에는 intellij 를 써서 실습을 해보았다.

## [2-01 스프링부트 프로젝트의 구조](https://wikidocs.net/160947)

### src/main/java 디렉터리

자바 파일을 작성하는 공간. 컨트롤러, 폼과 DTO, 데이터베이스 처리를 위한 엔티티, 서비스 파일 등이 있다.

### SbbApplication.java 파일

시작을 담당하느느 파일. <프로젝트명> + Application.java.
SbbApplcation 클래스 위에는 반드시 `@SpringBootApplication` 애너테이션이 적용되어 있어야 한다.
이 애너테이션을 통해 스프링부트의 모든 설정이 관리된다.

### src/main/resources 디렉터리

HTML, CSS, JavaScript, 환경파일 등을 작성하는 공간이다.

### templates 디렉터리

템플릿 파일을 저장한다. HTML 파일 형태로 자바 객체와 연동되는 파일.

### static 디렉터리

프로젝트의 스타일 시트(.css), 자바스크립트(.js) 그리고 이미지 파일(.jpg, .png) 등을 저장하는 공간이다.

### application.properties 파일

application.properties 파일은 환경을 설정한다. 프로젝트의 환경, 데이터베이스 등의 설정을 이 파일에 저장한다.

### src/test/java 디렉터리

프로젝트에서 작성한 파일을 테스트하기 위해 테스트 코드를 작성하는 공간이다. JUnit 과 스프링부트의 테스팅 도구를 사용하여 서버를 실행하지 않은 상태에서 src/main/java 디렉터리에 작성한 코드를 테스트할 수 있다.

### build.gradle 파일

그레이들(Gradle)이 사용하는 환경 파일이다. build.gradle 파일에는 프로젝트를 위해 필요한 플러그인과 라이브러리 등을 기술한다.

## [2-02 컨트롤러](https://wikidocs.net/160543)

```Java
package com.mysite.sbb;

import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.GetMapping;

@Controller
public class MainController {

    @GetMapping("/sbb")
    public void index() {
        System.out.println("index");
    }
}
```

자바 클래스에 `@Controller` 애너테이션을 적용하면 MainController 클래스는 스프링부트의 컨트롤러가 된다. 메서드의 `@GetMapping` 애너테이션은 요청된 URL과의 매핑을 담당한다. 서버에 요청이 발생하면 스프링부트는 요청 페이지와 매핑되는 메서드를 컨트롤러를 대상으로 찾는다.

여기서 `http://localhost:8080/sbb` URL 을 호출하면 500 오류 코드가 뜬다. URL 과 매핑된 함수는 결괏값을 리턴해야 하는데 아무런 값도 리턴하지 않기 떄문이다. 오류를 해결하려면 클라이언트(브라우저)로 응답을 리턴해야 한다.

```Java
package com.mysite.sbb;

import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.ResponseBody;

@Controller
public class MainController {

    @GetMapping("/sbb")
    @ResponseBody
    public String index() {
        return "index";
    }

}
```

응답으로 "index" 라는 문자열을 브라우저에 출력하기 위해 index 함수의 리턴값을 String 으로 변경하고 "index" 라는 문자열을 리턴했다. `@ResponseBody` 애너테이션은 URL 요청에 대한 응답으로 문자열을 리턴하라는 의미이다.

## [2-03 JPA](https://wikidocs.net/161164)

웹 서비스는 데이터를 처리할 때 대부분 데이터베이스를 사용한다.
그런데 데이터베이스를 사용하려면 SQL 쿼리(query)라는 구조화될 질의를 작성하고 실행하는 등의 복잡한 과정이 필요하다. 이떄 ORM(object relational mapping)을 이용하면 자바 문법만으로도 데이터베이스를 다룰 수 있다. 즉, ORM을 이용하면 개발자가 쿼리를 직접 작성하지 않아도 데이터베이스의 데이터를 처리할 수 있다.

question 테이블에 새로운 데이터를 삽입하는 쿼리는 보통 다음처럼 작성한다.

```SQL
insert into question (subject, content) values ('안녕하세요', '가입 인사드립니다 ^^');
insert into question (subject, content) values ('질문 있습니다', 'ORM이 궁급합니다');
```

하지만 ORM을 사용하면 쿼리 대신 자바 코드로 다음처럼 작성할 수 있다.

```Java
Question q1 = new Question();
q1.setSubject("안녕하세요");
q1.setContent("가입 인사드립니다 ^^");
this.questionRepository.save(q1);

Question q2 = new Question();
q2.setSubject("질문 있습니다");
q2.setContent("ORM이 궁금합니다");
this.questionRepository.save(q2);
```

이렇게 하면 별도의 SQL 문법을 배우지 않아도 된다.

코드에서 Question은 자바 클래스이며, 이처럼 데이터를 관리하는 데 사용하는 ORM 클래스를 엔티티(Entity)라고 한다. ORM을 사용하면 내부에서 SQL 쿼리를 자동으로 생성해 주므로 직접 작성하지 않아도 된다. 즉, 자바만 알아도 데이터베이스에 질의할 수 있다.

> > ORM의 장점
> > ORM을 이용하면 데이터베이스 종류에 상관 없이 일관된 코드를 유지할 수 있어서 프로그램을 유지\*보수하기가 편리하다. 또한 내부에서 안전한 SQL 쿼리를 자동으로 생성해 주므로 개발자가 달라도 통일된 쿼리를 작성할 수 있고 오류 발생률도 줄일 수 있다.

### JPA 란?

스프링부트는 JPA(Java Persistence API)를 사용하여 데이터베이스를 처리한다. JPA는 자바 진영에서 ORM(Object-Relational Mapping)의 기술 표준으로 사용하는 인터페이스의 모음이다..

> > JPA는 인터페이스이다. 따라서 인터페이스를 구현하는 실제 클래스가 필요하다. JPA를 구현한 대표적인 실제 클래스에는 하이버네이트(Hibernate)가 있다.

## [2-04 엔티티](https://wikidocs.net/161164)

엔티티(Entity)는 데이터베이스 테이블과 매핑되는 자바 클래스를 말한다.

> > 엔티티는 모델 또는 도메인 모델이라고 부르기도 한다.

### 질문 엔티티 작성하기

```Java
package com.mysite.sbb;

import java.time.LocalDateTime;

import jakarta.persistence.Column;
import jakarta.persistence.Entity;
import jakarta.persistence.GeneratedValue;
import jakarta.persistence.GenerationType;
import jakarta.persistence.Id;

import lombok.Getter;
import lombok.Setter;

@Getter
@Setter
@Entity
public class Question {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Integer id;

    @Column(length = 200)
    private String subject;

    @Column(columnDefinition = "TEXT")
    private String content;

    private LocalDateTime createDate;
}
```

`@Entity` 애너테이션을 적용해야 JPA 가 엔티티로 인식한다.
롬복의 `@Getter`, `@Setter` 애너테이션을 적용하면 Getter, Setter 메서드를 자동으로 생성해 준다.

> > 컨트롤러에 `@Controller` 애너테이션을 적용하는 것과 마찬가지로 엔티티는 `@Entity` 애너테이션을 적용해야 한다.

### @Id

고유 번호 id 속성에 적용한 @Id 애너테이션은 id 속성을 기본 키로 지정한다. 기본 키로 지정하면 이제 id 속성의 값은 데이터베이스에 저장할 때 동일한 값으로 저장할 수 없다. 고유 번호를 기본 키로 한 이유는 고유 번호는 엔티티에서 각 데이터를 구분하는
유효한 값으로 중복되면 안 되기 때문이다.

> > 데이터베이스에서는 id 와 같은 특징을 가진 속성을 기본 키 (primary key) 라고 한다.

### @GeneratedValue

`@GeneratedValue` 애너테이션을 적용하면 데이터를 저장할 때 해당 속성에 값을 따로 세팅하지 않아도 1씩 자동으로 증가하여 저장된다. `strategy` 는 고유번호를 생성하는 옵션으로 `GeneratedType.IDENTITY`는 해당 컬럼만의 독립적인 시퀀스를 생성하여 번호를 증가시킬 때 사용한다.

> > strategy 옵션을 생략할 경우에 `@GeneratedValue` 애너테이션이 지정된 컬럼들이 모두 동일한 시퀀스로 번호를 생성하기 때문에 일정한 순서의 고유번호를 가질 수 없게 된다. 이러한 이류로 보통 `GeneratedType.IDENTITY`를 많이 사용한다.

### @Column

엔티티의 속성은 테이블의 컬럼명과 일치하는데 컬럼의 세부 설정을 위해 `@Column` 애너테이션을 사용한다. length 는 컬럼의 길이를 설정할 때 사용하고 columnDefinition 은 컬럼의 속성을 정의할 때 사용한다. `columnDefinition = "TEXT"` 은 "내용"처럼 글자 수를 제한할 수 없을 때 사용한다.

> > 엔티티의 속성은 `@Column` 애너테이션을 사용하지 않더라도 테이블 컬럼으로 인식한다. 테이블 컬럼으로 인식하고 싶지 않은 경우에만 `@Transient` 애너테이션을 사용한다.

- 테이블의 컬럼명
- createDate 속성은 create*date 가 된다. 카멜케이스(Camel Case) 이름은 create_date 처럼 모두 소문자로 변경되고 언더바(*)로 단어가 구분되어 실제 테이블 컬럼명이 된다.

- 엔티티와 Setter
- 일반적으로 엔티티에는 Setter 메서드를 구현하지 않고 사용하기를 권한다. 엔티티는 데이터베이스와 바로 연결되어 있으므로 데이터를 자유롭게 변경할 수 있는 Setter 메서드를 허용하는 거시 안전하지 않다고 판단하기 때문이다. 엔티티를 생성할 경우에는 롬복의 `@Builder` 어노테이션을 통한 빌드패턴을 사용하고, 데이터를 변경해야 할 경우에는 그에 해당되는 메서드를 엔티티에 추가하여 데이터를 변경하면 된다.

### 답변 엔티티 생성하기

```Java
package com.mysite.sbb;

import java.time.LocalDateTime;

import jakarta.persistence.Column;
import jakarta.persistence.Entity;
import jakarta.persistence.GeneratedValue;
import jakarta.persistence.GenerationType;
import jakarta.persistence.Id;

import lombok.Getter;
import lombok.Setter;

@Getter
@Setter
@Entity
public class Answer {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Integer id;

    @Column(columnDefinition = "TEXT")
    private String content;

    private LocalDateTime createDate;

    private Question question;

}
```

question 속성은 답변 엔티티에서 질문 엔티티를 참조하기 위해 추가했다.
예를 들어 답변 객체 (예: answer) 를 통해 질문 객체의 제목을 알고 싶다면 `answer.getQuestion().getSubject()`처럼 접근할 수 있다. 하지만 이렇게 속성만 추가하면 안되고 질문 엔티티와 연결된 속성이라는 것을 명시적으로 표시해야 한다.

즉, 다음과 같이 question 속성에 `@ManyToOne` 애너테이션을 추가해야 한다.

```Java
(... 생략 ...)
import jakarta.persistence.ManyToOne;
(... 생략 ...)

@Getter
@Setter
@Entity
public class Answer {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Integer id;

    @Column(columnDefinition = "TEXT")
    private String content;

    @CreatedDate
    private LocalDateTime createDate;

    @ManyToOne
    private Question question;
}
```

답변은 Many 가 되고 질문은 One 이 된다.
따라서 `@ManyToOne`은 N:1 관계라고 할 수 있다. 이렇게 `@ManyToOne` 애너테이션을 설정하면 Answer 엔티티의 question 속성과 Question 엔티티가 서로 연결된다. (실제 데이터베이스에서는 ForeignKey 관계가 생성된다.)

> > `@ManyToOne` 은 부모 자식 관계를 갖는 구조에서 사용한다. 여기서 부모는 Question, 자식은 Answer 라고 할 수 있다.

그렇다면 반대방향, 즉 Question 엔티티에서 Answer 엔티티는 참조할 수는 없을까?

가능하다. 답변과 질문이 N:1 의 관계라면 질문과 답변은 1:N 의 관계라고 할 수 있다. 이런 경우는 `@ManyToOne` 이 아닌 `@OneToMany` 애너테이션을 사용한다. Question 하나에 Answer 는 여러 개이므로 Question 엔티티에 추가할 답변의 속성은 List 형태로 구성해야 한다.

```Java
package com.mysite.sbb;

import java.time.LocalDateTime;
import java.util.List;

import jakarta.persistence.CascadeType;
import jakarta.persistence.Column;
import jakarta.persistence.Entity;
import jakarta.persistence.GeneratedValue;
import jakarta.persistence.GenerationType;
import jakarta.persistence.Id;
import jakarta.persistence.OneToMany;

import lombok.Getter;
import lombok.Setter;

@Getter
@Setter
@Entity
public class Question {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Integer id;

    @Column(length = 200)
    private String subject;

    @Column(columnDefinition = "TEXT")
    private String content;

    private LocalDateTime createDate;

    @OneToMany(mappedBy = "question", cascade = CascadeType.REMOVE)
    private List<Answer> answerList;

}
```

Answer 엔티티 객체로 구성된 answerList 를 속성으로 추가하고 `@OneToMany` 애너테이션을 설정했다. 이제 질문 객체 (예: question) 에서 답변을 참조하려면 `question.getAnswerList()`를 호출하면 된다.
`@OneToMany` 애너테이션에 사용된 mappedBy 는 참조 엔티티의 속성명을 의미한다. 즉, Answer 엔티티에서 Question 엔티티를 참조한 속성명 question 을 mappedBy 에 전달해야 한다.

- CascadeType.REMOVE
- 질문 하나에는 여러개의 답변이 작성될 수 있다. 이때 질문을 삭제하면 그에 달린 답변들도 모두 함께 삭제하기 위해서 `@OneToMany` 속성으로 `cascade = CascadeType.REMOVE` 를 사용했다.
