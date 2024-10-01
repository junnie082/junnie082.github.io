---
layout: post
title: Java Spring - 1
subtitle: Java Spring 공부
author: Jun
categories: Java Spring
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
tags: Essay
sidebar: []
---

[참고 자료: GDG on Campus: Seoultech Backend 세션 자료](https://www.notion.so/saeyeonn/GDSC-Backend-25f6f5de8ec7418f92ea2b6ec5c5e0b8?p=f763b671f9124f87b2fccf67ae77008c&pm=s)
필사

## Spring 이란?

Spring은 자바 플랫폼을 위한 오픈 소스 애플리케이션 프레임워크

## Spring Boot란?

Spring Boot는 Spring 프레임워크를 더욱 쉽게 사용할 수 있도록 도와주는 확장 프로젝트. 스프링 부트는 스프링(Spring) 프레임워크에 톰캣(Tomcat)이라는 서버를 내장하고 여러 편의 기능들을 추가하여 꾸준한 인기를 누리고 있다.

[톰캣(Tomcat)이란?](https://velog.io/@hsk2454/Tomcat이란)

## Tomcat

### Tomcat이란?

- 아파치 소프트웨어 재단의 웹 어플리케이션 서버 (Web Application Server, WAS)
- 자바 서블릿을 실행시키고 JSP 코드가 포함되어 있는 동적 웹 페이지를 구동시켜주는 프로그램
- 내장되어 있는 웹 서버를 이용해 독립적으로 사용될 수도 있으나 아파치 (httpd), Nginx 등의 웹 서버와 함께 사용할 수도 있음

### Tomcat의 구조

- Coyote (HTTP Component): Tomcat에 TCP를 통한 프로토콜 지원
- Catalina (Servlet Container): 자바 서블릿을 호스팅하는 환경
- Jasper (JSP Engine): 실제 JSP 페이지의 요청을 처리하는 Servlet

### Tomcat의 동작

- HTTP 요청을 Coyote 에서 받아서 Catalina로 전달
- Catalina에서 전달받은 HTTP 요청을 처리할 웹 어플리케이션을 찾고 WEB-INF/web.xml 파일 내용을 참조하여 요청을 전달
- 요청된 Servlet을 통해 생성된 JSP 파일들이 호출될 때 Jasper가 Validation Check/Compile 등을 수행

### 처리순서

- HTTP > request > Catalina > Context > Servlet > Response

```
Tomcat은 JVM 위에서 동작

하나의 JVM에서 하나의 Tomcat Instance가 하나의 Process로 동작

하나의 Server에는 여러 개의 Service가 존재 가능, 각각의 Service는 1개의 Engine과 여러 개의 Connector로 구성

Engine은 Catalina Servlet Engine이라고도 불리며, 정의된 Connector로 들어온 요청을 하위에 있는 해당 Host에게 전달해주는 역할을 수행

하나의 Engine에는 여러 개의 Host가 존재 가능, Context는 하나의 Web Application을 나타내며 주로 *.war 파일의 형태로 배포

Tomcat Server가 요청을 받으면, Catalina (Tomcat Engine)가 요청에 맞는 Context (Context path)를 찾고, Context는 자신이 설정된 어플리케이션의 development descriptor file (web.xml)을 기반으로 전달받은 요청을 서블릿에게 전달하여 처리
```

### Embedded Tomcat

- 톰캣은 기본적으로 Java로 개발되어 있음
- 위에서 설명한 일반적인 톰캣말고 임베디드 톰캣을 사용하면 웹 어플리케이션에 내장시켜서 어플리케이션과 동일한 JVM에서 실행이 가능
- 마이크로서비스에 적합
- Spring boot에서는 기본적으로 Embedded Tomcat이 포함되어 있음

### Tomcat과 Embedded Tomcat의 창

- 성능 상 유의미한 차이 없음
- 임베디드 톰캣은 virtual host가 지원되지 않음
- 임베디드 톰캣은 WAS 설정을 웹 어플리케이션 내부에서 해야함 (Java Code, application.properties 등)
- 외장 톰캣은 xml 파일로 WAS 설정을 할 수 있음
- 부팅 속도는 Embedded Tomcat이 좀 더 빠름

## API와 REST API

API는 Application programming interface의 약자로 애플리케이션을 프로그래밍하는 데 쓰이는 인터페이스. 인터페이스는 쉽게 말해 노트북 화면, 키보드 등 사용자와 기기를 연결해주기 위한 중간 역할을 하는 지점.
REST API는 API를 다양한 사람들이 사용하는 만큼 규칙과 내용을 더 간단하고 쉽게 만든 것이다.
HTTP 메서드와 명사로 표현한다.

예시: `GET http://도메인주소/classes/2/students` -> 'GET'을 사용하면서 2반의 학생들의 데이터를 불러오는 요청

## HTTP와 사용자 - 서버 통신 과정

### 클라이언트-서버 통신

우리가 사이트에 들어가서 상품 조회 버튼을 클릭하면 서버로 리소스나 데이터를 요청한다. 서버는 요청을 받아 리소스와 데이터를 클라이언트(나)에게 전달한다. 요청-응답 방식으로 통신이 이루어지는데, 어떤 식으로 이루어지는 걸까?

### 프로토콜(protocol)

통신 방법에 차이점이 생긴다면 데이터(리소스)를 교환하는 것에 문제가 생길 것이다. 나는 A 방식으로 요청을 했는데 B 방식으로 응답을 보내준다면 나는 해당 데이터를 어떻게 해야될지 고민해야할 것이고, 정상적으로 받기 위한 방법을 항시 생각해 보아야만 한다. 그래서 다른 컴퓨터 간 (클라이언트 - 서버 간)에 통신약속을 미리 해둔 것이 바로 `프로토콜`이다. 이 프로토콜이라는 것은 한 가지 유일한 것이 아니라 사용되는 환경에 따라 규약을 정해두고 있다는 이야기다.

### 웹 애플리케이션 프로토콜: HTTP

웹 애플리케이션 아키텍처에서 클라이언트와 서버 간에 통신하기 위해 만들어진 것이 HTTP 프로토콜이다. 클라이언트와 서버는 이를 기준으로 데이터를 요청하고, 제공한다.

HTTP (Hypertext Transfer Protocol)은 웹에서 브라우저(클라이언트)와 서버가 데이터를 주고받기 위한 규약이다.

### HTTP 메서드

서버가 수행해야 할 동작을 지정하여 요청을 보내는 방법

- GET: 리소스 조회
- POST: 데이터 추가, 등록
- PUT: 리소스 수정
- DELETE: 리소스 삭제

### HTTP 상태코드

클라이언트(프론트)가 보낸 요청이 성공했는지 실패했는지 서버에서 알려주는 숫자 코드이다. 프론트와의 규칙이라고 생각하자

1XX: 요청이 수신되어 처리중  
2XX: 요청 정상 처리  
3XX: 요청을 완료하려면 추가 행동이 필요  
4XX: 클라이언트 오류로 인해 서버가 요청 수행 불가  
5XX: 서버 오류, 서버가 정상 요청을 처리하지 못함

### JSON

데이터를 프론트엔드와 주고 받을 때 사용되는 형식
직렬화: 객체를 JSON 형식으로 변환
역직렬화: JSON을 객체로 변환

```
{
    "email": "nmkk1234@naver.com",
    "password": 123
}
```

### 스프링 API 설계 구조 - Layered Architecture

Layered Architecture란 계층으로 나뉜 형태의 아키텍쳐이다. 각 레이어는 하나의 관심사에만 집중할 수 있도록 하는 것을 목표로 한다.

- 표현계층 - Controller: 사용자의 요청을 처리
- 응용계층 - Service: 비즈니스 로직을 정의
- 도메인 계층 - Model(Entity): 도메인의 정보 보유
- 인프라 계층 - Repository: DB와의 통신 담당

Entity - Controller - Service - Repository 4개로 나누어서 코딩함.

### application.yml

application.yml 파일은 qna 프로젝트의 환경을 설정한다. 환경변수, 데이터베이스 등의 설정을 이 파일에 저장한다.

### JPA

스프링 부트는 JPA (Java Persistence API)를 사용하여 데이터베이스를 관리한다. 스프링 부트는 JPA를 ORM(Object-Relational Mapping) 기술의 표준으로 사용한다.

### ORM

Object Relational Mapping의 약자이며 객체와 관계형 데이터를 매핑하기 위한 기술명이다. 데이터베이스에서 데이터를 가져올 때 SQL 문인 SELECT \* FROM user; 를 실행해야 하지만 ORM을 사용하면 user.findAll() 라는 메서드 호출로 데이터를 가져올 수 있다.
결국 SQL문이 아닌 직관적인 코드로 데이터를 조작할 수 있게 해준다.

### H2

JPA를 사용해 데이터를 관리하려면 데이터베이스를 설치해야 한다. 여기서 MySQL 등의 굵직한 데이터베이스보다 설치하기 쉽고 사용하기도 편리한 H2 데이터베이스를 사용한다.

### Bean

빈(Bean)은 스프링 컨테이너에 의해 관리되는 재사용 가능한 소프트웨어 컴포넌트이다. 즉, 스프링 컨테이너가 관리하는 자바 객체를 뜻하며, 하나 이상의 빈(Bean)을 관리한다.
빈은 인스턴스화된 객체를 의미하며, 스프링 컨테이너에 등록된 객체를 스프링 빈이라고 한다. 쉽게 이해하자면 new 키워드 대신 사용한다고 보면 된다.

### lombok

여러가지 어노테이션을 제공하고 컴파일 과정에서 자동으로 개발자가 원하는 메소드를 생성/주입 방식으로 동작하는 라이브러리

- @Getter: getter 자동생성
- @Setter: setter 자동생성
- @NoArgsConstructor: 매개변수 없는 기본생성자 자동생성
- @AllArgsConstructor: 모든 필드를 파라미터로 받는 생성자 자동생성
- @RequiredArgsConstructor: final이나 @NonNull인 필드만 매개변수로 받는 생성자 자동생성
- @NonNull: null을 허용하지 않는 객체 Bean 자동생성
- @Nullable: null을 허용하는 객체 Bean 자동생성
- @Data: @Getter, @Setter, @RequiredArgsConstructor, @ToString, @EqualsAndHashCode을 한꺼번에 설정해주는 어노테이션
- @ToString: toString 메소드 자동생성
- @EqualsAndHashCode: equals, hashCode 메서드 생성
- @Builder: 자동으로 해당 클래스에 빌더 추가

```
사용 전

public class UserDto {
    private String id;
    private String pwd;

    public String getId() {
        return id;
    }

    public void setId(String id) {
        this.id = id;
    }

    public String getPwd() {
        return pwd;
    }

    public String setPwd(String pwd) {
        this.pwd = pwd;
    }
}
```

```
사용 후

@Getter
@Setter
public class UserDto {
    private String id;
    private String pwd;
}
```

### 엔티티 테이블 매핑

엔티티는 데이터베이스 테이블과 매핑되는 자바 클래스이다. 회원가입 시에 데이터베이스에 어떤 속성들이 필요한지 생각해보자. 사용자의 이메일과 비밀번호 그리고 화면에 이메일 대신 표시할 닉네임이 필요할 것이다.

- @Entity: 스프링 부트가 User 클래스를 엔티티로 인식. 스프링 실행시 JPA가 데이터베이스에 해당 클래스를 테이블로 생성한다.

- @Getter: Getter 메서드를 자동으로 생성

- @Id: id 속성을 기본키로 지정한다. id 속성의 고유 번호들은 엔티티에서 데이터들을 구분하는 유효한 값으로, 중복되면 안되기 때문이다.

- @Column: 테이블 열의 세부 설정을 위해 사용한다. unique = true는 유일한 값만 저장할 수 있음을 의미한다.

- @Builder: User 객체를 생성할 때 체이닝 방식으로 만들 수 있게 해주는 애너테이션이다.

```
// user/domain/User.java

@Getter
@Entity
@NoArgsConstructor(access = AccessLevel.PROTECTED)
@Table(name = "users")
public class User {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    @Column(unique = true)
    private String email;

    private String email;

    private String password;

    @Column(unique = true)
    private String username;

    @Builder
    public User(String username, String email, String password) {
        this.username = username;
        this.email = email;
        this.password = password;
    }
}
```

```
// resources/application.yml
// H2 DB의 콘솔을 웹에서 확인 가능

spring:
  h2:
    console:
      enabled: true
      path: /h2-console

// H2 데이터베이스에 로그인하기 위해 사용자이름과 비밀번호 지정
datasource:
  url: jdbc:h2:mem:qna;NON_KEYWORDS=USER
  username: sa
  password:
  driver-class-name: org.h2.Driver
```

### DTO(Data Transfer Object)와 Bean Validation

DTO란 데이터를 전달하는 용도의 객체이다. 비즈니스 로직을 포함하지 않는 단순한 객체라고 생각하면 된다.
엔티티를 사용하지 않고 DTO를 사용하는 이유는 이후에 설명할 빈 검증을 사용하면 엔티티 코드가 복잡해져서 한눈에 보기 어렵다.
원하는 데이터만 표시해서 가독성을 높이기 위해 사용한다.

Bean Validation은 DTO의 필드에 애너테이션을 달아서 요청 내용을 개발자가 원하는 조건에 맞추었는지 검증한다. 주로 '특정 값이 비었는지', '특정 범위 안인지'를 검증한다.

`username`은 입력받는 데이터의 길이가 3~25 사이여야 한다는 검증 조건을 설정했다. `@Size`는 문자열의 길이가 최소 길이 (`min`)와 최대 길이(`max`) 사이에 해당하는지를 검증한다.

`password1`과 `password2`는 '비밀번호'와 '비밀번호 확인'에 대한 속성이다. 로그인할 때는 비밀번호가 한 번만 필요하지만 회원 가입 시에는 입력한 비밀번호가 정확한지 확인하기 위해 2개의 필드가 필요하므로 이와 같이 작성한다. 그리고 `email` 속성에는 `@Email` 애너테이션이 적용되었다. `@Email`은 해당 속성의 값이 이메일 형식과 일치하는지를 검증한다.

```
// user/dto/LoginRequest.java

@Getter
public class LoginRequest {
    @NotEmpty(message = "이메일은 필수항목입니다.")
    @Email(message = "올바른 이메일 형식을 적어주세요.")
    private String email;

    @NotEmpty(message = "비밀번호는 필수항목입니다.")
    private String password;
}
```

```
// user/dto/SignupRequest.java
@Getter
@Builder
public class SignupRequest {

    @Size(min = 3, max = 25)
    @NotEmpty(message = "사용자ID는 필수항목입니다.")
    private String username;

    @NotEmpty(message = "비밀번호는 필수항목입니다.")
    private String password1;

    @NotEmpty(message = "비밀번호 확인은 필수항목입니다.")
    private String password2;

    @NotEmpty(message = "이메일은 필수항목입니다.")
    @Email(message = "이메일 형식이 올바르지 않습니다.")
    private String email;
}
```

```
// user/dto/userInfo.java
@Getter
@Builder
public class UserInfo {
    private Long id;
    private String email;
    private String username;
}
```
