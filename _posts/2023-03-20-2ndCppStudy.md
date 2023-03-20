---
layout: post
title: 두 번째 C++ 스터디, 자료형과 연산자
subtitle: 2023 TCP C++ 스터디 2주차
author: Jun
categories: C++
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
tags: C++
sidebar: []
---

# 2023.03.20.(월)



### 자료형이란??


자료형 또는 데이터 타입(data type)은 실수, 정수, 불린(boolean) 자료형 등 여러 종류의 데이터를 식별하는 분류이다.

자료형은 일반적으로 다음을 포함한다.

* 정수 (integer)
* 불린 (boolean)
* 문자 한 개 (character)
* 부동소수점, 실수 (floating-point number)
* 숫자, 문자로 이루어진 문자열 (string)

[자료형이란? 위키백과](https://ko.wikipedia.org/wiki/자료형)





### 자료형의 종류

자료형(Data Type)이란 변수의 종류를 의미한다. 변수에 값을 담기 이전에, 정수, 실수, 문자, 문자열 등 어떤 값들을 지닐 수 있는지 자료형을 미리 정해주어야 한다. 

[자료형](https://opentutorials.org/module/3921/23515)

![problem](/assets/images/banners/2023-03-20/img1.png)


# 정수형

* `char` 은 전수와 문자를 표시할 때
* `short, int, long, long long`은 정수, 즉 숫자를 나타낼 때 (차이점은 '좀 더 크거나 작은 숫자를 표시')

|   구분   ||   명칭  ||  설명   :|
|:-------- |:------ |:-------- |
|부호가 있는 변수| signed |  기본(default) 형식  |
|부호가 없는 변수| unsigned |  음수를 표현할 수 없고, 양수 값의 표현범위가 두 배 정도 늘어남 |

정수형의 경우 `signed(부호 있는 변수)`, `unsigned(부호 없는 변수)`로 나뉘는데 signed의 경우에는 음수와 양수 둘 다 표현이 가능하고, unsigned의 경우에는 양수만을 표현할 수 있는 대신에 범위가 2배 정도 늘어난다. 

`short(signed short)`의 경우에는 표현 범위가 -32,768 ~ 32,767 까지지만 `unsigned short`의 경우에는 음수를 제외하고 0 ~ 65,535 까지 표현이 가능하다. 

실수형은 `float, double, long double`순으로 좀 더 큰 숫자, 많은 소수점을 나타낼 수 있으며, 정수형과 달리 `unsigned`가 존재하지 않는다. 





[자료형의 종류](https://edu.goorm.io/learn/lecture/201/한-눈에-끝내는-c언어-기초/lesson/5973/자료형이란)



## 적절한 연산자 붙이기

이름

학번

과목

학점
  
입력) 
전효정  
21101223  
자료구조  
A  

출력)
21101223 '전효정'님은, '자료구조' 과목에서 A 학점을 받으셨습니다. 




### 연산자


[연산자란] (http://prof.dongju.ac.kr/syhong/public_html/teaching/c/c04.htm)


* 산술 연산자 (+, -, *, /, %)
* 논리 연산자 (<, <=, ==, >, !=)
* 관계 연산자 (||, &&, !)
* 증감 연산자 (++, --)
* 대입 연산자 (=)

등등...


|   종류   ||   설명  ||  보기   :|| 의미 |
|:--------|:--------|:--------|:--------|
|   ++    |  1씩 증가 |  x++, ++x  |  x = x+1 |
|   --    |  1씩 감소 |  x--, --x  |  x = x-1 |
|  +, -   |  부호 표시 |  +x, -x  |           |


## 단항 연산자

* 후행 증감 연산자: 변수의 값을 먼저 사용하고 난 후 그 변수의 값을 증가 시키거나 감소 시킨다.
* 선행 증감 연산자: 변수의 값을 먼저 증가 시키거나 감소 시킨 후 그 변수를 사용한다.


예제)

# 1.   

```C++
int x = 1;  
int y;

x = x++;  
y = x;   
```  

`x 의 값은? y 의 값은?`


# 2.    

```C++
int x = 1; 
int y; 

x = ++x;  
y = x;  
```

`x 의 값은? y 의 값은?`



## 대입 연산자

`=`과 `==`의 차이는?

int x = 1;
int y = 2;
int temp; 

temp == x;
x == y; 
y == temp; 

# 올바르게 바꾸어 x 와 y 값이 바뀌도록 하기. 


무엇이 틀렸을까? 

그렇다면 `==`은 어디에 쓸까? (관계 연산자)

```C++
if (x == y) {
    cout << "The values are the same";
}
```


# 복합 대입문

* +=  ( x += y  ---->  x = x + y)
* -=  ( x -= y  ---->  x = x - y)
* %=  ( x %= y  ---->  x = x % y)
* *=  ( x *= y  ---->  x = x * y)


# 관계 연산자 (relational operator)

* 두 식의 대소 크기를 비교하는 연산자로서 연산 결과가 참(true)이나 거짓(false)으로 표현한다.
* 참(true)은 0이 아닌 모든 수를 의미하여, 거짓(false)은 0을 의미한다.


* >
* >=  
* <  
* <=   
* ==  
* !=  


# 논리 연산자

* && 논리 곱(AND)  
* || 논리 합(OR)  
* ! 논리 부정(NOT)  

예제) 
true && true
true && false
false && false

true || true
true || false
false || false  

!true  
!false  


# 비트 연산자

* &
* |
* ^  
* ~  

* >>  
* <<  



### 문제를 풀어보며 C++ 의 '자료형' 및 '연산자'와 친해지기

백준 그룹 -> TCP C++ 스터디 -> 2주차

[백준 2주차, 자료형과 연산자](https://www.acmicpc.net/group/workbook/view/17067/55434)