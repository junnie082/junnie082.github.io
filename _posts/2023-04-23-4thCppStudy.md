---
layout: post
title: 네 번째 C++ 스터디, 함수
subtitle: 2023 TCP C++ 스터디 4주차
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

[함수의 정의](http://www.tcpschool.com/cpp/cpp_function_basic)


### 함수(Function)란??

* 반복적인 프로그래밍을 피할 수 있다.
* 프로그램을 여러 개의 함수로 나누어 작성하면, 모듈화로 인해 전체적인 코드의 가독성이 좋아진다.
* 프로그램에 문제가 발생하거나 기능의 변경이 필요할 때에도 손쉽게 유지보수 할 수 있다.

```C++
int sum(int x, int y) {

}
```

위에서 int 부분은 `반환 자료형`, sum 부분은 `함수 이름`, 소괄호 () 안에 있는 것들은 `매개변수` 라고 한다.   
대괄호 {} 안의 부분은 `함수 몸체`라고 한다. 

1. 반환 타입(return type): 함수가 모든 작업을 마치고 반환하는 데이터의 타입을 명시한다.
2. 함수 이름: 함수를 호출하기 위한 이름을 명시한다.
3. 매개변수 목록(parameters): 함수 호출 시에 전달되는 인수의 값을 저장할 변수들을 명시한다.
4. 함수 몸체: 함수의 고유 기능을 수행하는 명령문의 집합이다.


*** 함수가 반환할 수 있는 값은 한 개를 넘지 못한다.
또한, 함수의 특성에 따라 인수나 반환값이 하나도 없는 함수도 존재할 수 있다. 

C+++ 에서는 반환값으로 배열을 제외한 모든 타입을 사용할 수 있습니다. 하지만 구조체나 객체에 포함된 배열은 반환할 수 없다. 



## 인수로 전달받은 두 수 중에서 더 작은 수를 반환하는 SmallNum() 함수

```C++
#include <iostream>
using namespace std; 

int SmallNum(int num1, int num2) 
{
    if (num1 <= num2) {
        return num1; 
    }
    else
    {
        return num2; 
    }
}

int main(void) 
{
    int result;

    result = SmallNum(4, 6); 
    cout << "두 수 중 더 작은 수는 " << result << "입니다." << endl;
    result = SmallNum(8, 6); 
    cout << "두 수 중 더 작은 수는 " << result << "입니다." << endl; 
    result = SmallNum(2, 8); 
    cout << "두 수 중 더 작은 수는 " << result << "입니다." << endl;
    return 0; 
}
```



### 숫자를 더하여 반환하는 함수 만들기. 

* 함수 이름은 sumTwoNumbers 로 합니다!
* 매개 변수는 어떻게 설정해야 할까요?
* 반환 타입은 어떻게 될까요?

함수로부터 얻은 값을 출력해 보세요. 


# 두 숫자를 더해야 하는 코드가 엄청 많이 필요하다면, 함수 안의 내용을 일일이 치는 것은 어렵겠죠.


### 원의 넓이를 구하는 함수 만들기.

* 함수 이름은 circleArea 로 합니다!
* 매개 변수는 어떻게 설정해야 할까요?
* 반환 타입은 어떻게 될까요?

함수로부터 얻은 값을 출력해 보세요. 


[함수의 사용법](https://coding-factory.tistory.com/637)

### 함수의 종류

* 사용자 정의 함수: 사용자가 구현하고 싶은 기능을 구현하는 것
* 라이브러리 함수: printf(), scanf() 같은 함수인데 헤더파일 안에 정의되어 있어 원하는 라이브러리를 사용하고 싶다면 헤더파일을 불러와 사용하면 됨
