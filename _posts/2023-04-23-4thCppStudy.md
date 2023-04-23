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


[프로토타입(Prototype)이란?](https://swdoodle.tistory.com/18)

### 함수 정의 위치의 중요성

```C++
#include <stdio.h>

void main()
{
	int result;
    	result = MySum(3, 4);
    	printf("%d", result);
}

int MySum(int a, int b)
{
	int sum;
    	sum = a + b;
    	return sum;
}
```

위 코드는 컴파일 에러가 나게 된다. 
`컴파일러는 위에서 아래로 컴파일을 진행하기 때문에` 컴파일러는 main 함수를 컴파일할 때, '나는 MySum 함수를 본 적이 없는데?' 라고 할 것이다.

즉, 함수는 호출되기 전에 미리 정의되어야 한다. 



### 프로토타입(Prototype)

프로그램을 개발하면서 많은 사용자 정의 함수를 만들다 보면 main 함수는 점점 아래로 밀릴 것이다.
그렇게 된다면 문서를 보기 힘들어지며, 또한 함수들이 많아지면 각 함수를 찾을 때 찾기 힘들어진다.

그래서 `프로토타입(Prototype)`이다.

```C++
#include <iostream>

int MySum(int a, int b); // 프로토타입

void main()
{
    int result; 
    result = MySum(3,4);
    cout << result;
}

int MySum(int a, int b)
{
    int sum; 
    sum = a + b;
    return sum; 
}
```

이렇게 main 함수 보다 위에 먼저 사용자 함수를 정의할 수 있는 것이 프로토타입이다.

이렇게 할 경우 위쪽엔 함수의 목록이 정리되어 매우 보기 좋을 뿐만 아니라, 함수의 내용에서 다른 사용자 함수를 호출하는 데 제약이 없어진다. 

### 프로토타입(Prototype)의 구조

`반환타입 함수이름(매개변수);`

프로토타입의 구조는 사용자 정의 함수의 구조와 비슷하다.
다른 점이라면 괄호 안에 함수 내용이 없고 맨뒤에 세미콜론(;)이 붙어 있다. 

프로토타입을 선언할 때는, 매개변수의 이름을 두 번이나 쓸 필요가 없기 때문에 매개변수를 순서에 맞게 자료형만 적어도 된다. 

프로토타입과 사용자 함수의 관계
* 매개변수의 개수가 같아야 한다. 
* 매개변수의 자료형이 같아야 한다. 
* 반환 타입이 같아야 한다. 
