---
layout: post
title: 첫 번째 C++ 스터디 
subtitle: 2023 TCP C++ 스터디 1주차
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

# 2023.03.12.(월)


* VS Code 설치

* [VSC 에서 C/C++ 코딩 환경 구축하기](https://daringfireball.net/projects/markdown/basics)




### C++ 란??

- 객체 지향 및 멀티 패러다임을 지원하는 프로그래밍 언어
- C언어에는 없는 객체지향 프로그래밍을 지원하기 위한 C언어의 확장판

개인적인 경험...

작년까지 C 를 사용하여 알고리즘 문제를 해결하다 보니...
스택, 큐, 덱 등등 기본적인 자료구조들까지도 직접 구현해야 했다. 



# 백준 10828번. 스택


{% highlight C %}

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

struct Stack {
	int value;
	struct Stack *next;
};

void push(struct Stack *head, int X)
{
	struct Stack *newNode = malloc(sizeof(struct Stack));
	newNode -> value = X;

	if (head -> next == NULL) {
		head -> next = newNode;
		newNode -> next = NULL;
	} else {
		newNode -> next = head -> next;
		head -> next = newNode;
	}
}

int pop(struct Stack *head) 
{
	int X; 
	struct Stack *target = head -> next;
	if (head -> next == NULL) return -1;

	X = target -> value;

	if (target -> next == NULL) {
		free(target);
		head -> next = NULL;
	} else {
		head -> next = target -> next;
		free(target);
	}
	return X;
}

int empty(struct Stack *head) {
	if (head -> next == NULL) return 1;
	else return 0;
}

int top(struct Stack *head) {
	if (head -> next == NULL) return -1;
	else return head -> next -> value; 
}

int main()
{
	char string[6];
	int X, N, size = 0;
	struct Stack *head = malloc(sizeof(struct Stack));
	head -> next = NULL;

	scanf("%d", &N);

	for (int i = 0; i < N; i++) {
		scanf("%s", string);

		if (!strcmp("push", string)) {
			scanf("%d", &X);
			push(head, X);
			size++;
		} else if (!strcmp("pop", string)) {
			printf("%d\n",pop(head));
			size--;
			if (size < 0) size++;
		} else if (!strcmp("size", string)) {
			printf("%d\n", size);
		} else if (!strcmp("empty", string)) {
			printf("%d\n", empty(head));
		} else {
			printf("%d\n", top(head));
		}
	}

	while (head -> next != NULL) {
		pop(head);
	} 
	free(head); 

}

{% endhighlight %}





C에는 스택에 대한 라이브러리가 따로 없어서, 이런 자료구조들을 모두 기본적인 '배열'이나 '연결 리스트' 등을 이용하여 직접 구현해 주어야 했다. 





{% highlight C++ %}

#include <iostream>
#include <stack>
using namespace std; 

int main()
{
	int N; 
	string str; 
	int num; 

	stack<int> s; 
	cin >> N; 
	for (int i = 0; i < N; i++) {
		cin >> str; 
		if (str.compare("push") == 0) {
			cin >> num;
			s.push(num);  
		} else if (str.compare("pop") == 0) {
			if (!s.empty()) {
				cout << s.top() << "\n"; 
				s.pop(); 
			} else cout << "-1\n"; 
		} else if (str.compare("size") == 0) {
			cout << s.size() << "\n"; 
		} else if (str.compare("empty") == 0) {
			if (s.empty()) cout << "1\n";
			else cout << "0\n"; 
		} else if (str.compare("top") == 0) {
			if (!s.empty()) cout << s.top() << "\n";
			else cout << "-1\n";  
		}
	}	
}

{% endhighlight %}

하지만 C++ 의 <stack> 을 쓰면 코드를 훨씬 더 간편하게 작성할 수 있다. 






## 그럼 C 말고 C++ 만 공부하면 되지 않을까요?

![problem](/assets/images/banners/2023-03-13/stack.png)


[C를 공부해야 하는 이유](https://therceres.tistory.com/8)
[C++를 공부해야 하는 이유](https://php-style.selfhow.com/post/?id=776)







### C로 입출력 해보기

<입력 예시>  
전효정  
21  

<출력 예시>  
21 학번 전효정님, 안녕하세요!  
우리 함께 열심히 C++ 공부를 해봅시다.  


### 위 코드를 C++ 로 바꾸어 보기  

* C 언어에서는 입력을 받을 때 scanf() 함수를 사용하였다. 그렇다면 C++ 에서는?  
* C 언어에서는 출력을 할 때 printf() 함수를 사용하였다. 그렇다면 C++ 에서는?  


{% highlight C++ %}

#include <iostream>

int main()
{
    
}

{% endhighlight %}


### 문제를 풀어보며 C++ 의 '입출력'과 친해지기

백준 그룹 -> TCP C++ 스터디 -> 1주차

백준 2557번. Hello World  
백준 10171번. 고양이  
백준 10172번. 개  
백준 10926번. ??!  
