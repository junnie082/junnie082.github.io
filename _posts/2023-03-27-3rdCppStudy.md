---
layout: post
title: 세 번째 C++ 스터디, 제어문 (while, for, switch)
subtitle: 2023 TCP C++ 스터디 3주차
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

# 2023.03.27.(월)






### 제어문


[제어문-조건문](https://min-zero.tistory.com/entry/C-기본-공부정리-4-1-제어문-조건문)

## if 문

```C++
if (조건)  {
    조건이 true 일 때 실행;
}
```


## if else 문

```C++
if (조건){
    조건이 true 일 때 실행;
}
else {
    조건이 false 일 때 실행; 
}
```


## else if 문

```C++
if (조건 1) {
    조건 1이 true 일 때 실행;
}
else if (조건 2) {
    조건 2가 true 일 때 실행; 
}
else if (조건 3) {
    조건 3이 true 일 때 실행; 
}
....
else {
    위 조건들이 모두 false 일 때 실행; 
}
```

## 과연 위 실행 코드들의 순서가 중요할까?

```C++
if (a >= 1) {

} else if (a >= 2) {

} else if (a >= 3) {

} else {

}
```

```C++
if (a >= 3) {

} else if (a >= 2) {

} else if (a >= 1) {

} else {

}
```

## a = 2 일 때, 둘의 코드는 어떻게 다른가?

if문 순차적으로 다음 아래 코드로 넘어가는 것을 확인할 수 있다.



## switch 문

```C++
switch (조건) {
    case 값 1:
        조건의 값이 1일 때 실행;
        break;
    case 값 2:
        조건의 값이 2일 때 실행; 
        break;
....
    default:
        위에서 해당하는 조건의 값이 없을 때 실행; 
        break;
}
```

표현식이 double 또는 float 값이 될 수 없다.

# break; 를 써주지 않으면?

```C++
int a = 2;
switch (a) {
    case 1:
        a = 10;
        break;
    case 2:
        a = 20;
    case 3:
        a = 30;
    case 4:
        a = 40;
    default:
        a = 100;
        break;
    
}
```



[제어문-반복문](https://min-zero.tistory.com/entry/C-기본-공부정리-4-1-제어문-반복문)


## while 문  

```C++  
while (조건) {  
    조건이 true 일 때 실행;  
}  
```  


```C++  
int i = 0;   
while (i < 10) {  
    cout << i << " ";  
    i++;  
}  
```  
 
```C++  
int i = 0;   
while (i < 10) {  
    cout << i << " ";  
    i += 2;   
}  
```  


조건문이 계속 참일 경우 반복문이 끝나지 않는 무한루프에 빠지므로 반복문이 종료될수 있도록 조건문을 잘 조절해야 한다.  



## do while 문  

```C++  
do {  
    한 번 실행 후,  
    조건이 true 면 실행; 
} while(조건);  
```  


## while 문과 do while 문의 차이점은 무엇일까??  

do while 문은 {} 안의 코드를 `무조건 한 번`은 실행하고 조건을 판별한다.  



## for 문  

```C++  
for (초기식; 조건문; 증감식) {  
    조건문이 true 면 실행;  
}  
```  

```C++  
for (int i = 0; i < 10; i++) {  
    cout << i << " ";  
}  
```  

```C++  
int arr[10] = {0};  
for (int i = 0; i < 10; arr[i++]);  
```  


```C++  
int i = 0;   
while (i < 10) {  
    cout << i << " ";  
    i += 2;   
}  
```  

# 위 코드를 for 문으로 바꾸면?  

```C++
for (int i = 0; i < 10; i += 2) {
    cout << i << " ";
}
```


## 반복문 제어 


## continue
이 코드가 진행되다 이 명령을 만날 경우 나머지 코드를 실행하지 않고 바로 조건식으로 건너뛰게 된다. 따라서 반복 중에 예외를 처리하기 위해 많이 사용된다.


# 1부터 10까지 출력하는데, 5만 출력하지 않으려면??  

```C++
for (int i = 1; i <= 10; i++) {
    if (i == 5) continue;
    cout << i << " ";
}
```


## break

반복문을 종료시킨 뒤 반복문 다음 코드로 진행된다.


# 숫자를 계속 입력 받다가, 0을 입력 받으면 반복문을 빠져나가게 하려면?  
  
  
```C++  
while (1) {  
    cin >> n;   
    if (n == 0) break;  
    cout << n << " ";   
} 
``` 



## goto

goto의 경우 아무런 제약 없이 cpu가 지정된 label로 점프하도록 하여 프로그램 실행의 흐름을 변경할 수 있다. 

 goto의 경우 스파게티 코드(스파게티 코드는 컴퓨터 프로그램의 소스 코드가 복잡하게 얽힌 모습을 스파게티의 면발에 비유한 표현이다. 스파게티 코드는 작동은 정상적으로 하지만, 사람이 코드를 읽으면서 그 코드의 작동을 파악하기는 어렵다.)가 될 수 있으므로 사용에 대해 부정적이다.

```C++
int main()
{
    int x = 1;
    goto skip;
    x = 0;
    cout << x << " ";

skip: 
    x = 10;
    cout << x << " ";
}
```


 
### 문제 풀며 반복문과 친해지기

[백준 3주차 - 제어문](https://www.acmicpc.net/group/workbook/view/17067/55822)