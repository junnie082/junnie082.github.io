---
layout: post
title: 로또 프로그램
subtitle: 2023 TCP 스프링스프링) Java Sprig 스터디
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
tags: Java Spring
sidebar: []
---

# 2023.03.05.(일)

2023년 목표, 나는 `백엔드 마스터`가 된다. 

백엔드를 공부하기에 앞서서, 나는 Java를 사실 배워본 적이 없다. 기껏해야 다룰 줄 아는 언어라고는 C, C++, Python 정도로, 사실상 Java 언어에 대한 이해부터 높여 나가야 한다. 

TCP 스피링스프링 첫 과제, 로또 만들기 프로그램은 이렇다: 



### 로또 프로그램



## 기능 요구 사항

- 로또는 3가지 종류의 로또가 있다.
  - 1. 작은 로또 2. 중간 로또 3. 큰 로또    
- 로또 번호의 숫자 범위는 1~45까지이다.
- 1개의 로또를 발행할 때 중복되지 않는 6개의 숫자를 뽑는다.
- 당첨 번호 추첨 시 중복되지 않는 숫자 6개와 보너스 번호 1개를 뽑는다.
- 당첨은 1등부터 5등까지 있다. 당첨 기준과 금액은 아래와 같다.
    - 작은 로또
    - 1등: 6개 번호 일치 / 2,000,000원
    - 2등: 5개 번호 + 보너스 번호 일치 / 30,000원
    - 3등: 5개 번호 일치 / 1,500원
    - 4등: 4개 번호 일치 / 500원
    - 5등: 3개 번호 일치 / 100원
    
    - 중간 로또
    - 1등: 6개 번호 일치 / 50,000,000원
    - 2등: 5개 번호 + 보너스 번호 일치 / 3,000,000원
    - 3등: 5개 번호 일치 / 150,000원
    - 4등: 4개 번호 일치 / 50,000원
    - 5등: 3개 번호 일치 / 5,000원
    
    - 큰 로또
    - 1등: 6개 번호 일치 / 2,147,000,000원
    - 2등: 5개 번호 + 보너스 번호 일치 / 850,000원
    - 3등: 5개 번호 일치 / 10,000원
    - 4등: 4개 번호 일치 / 0원
    - 5등: 3개 번호 일치 / 0원

* 로또 구입 금액을 입력하면 구입 금액에 해당하는 만큼 로또를 발행해야 한다.
* 로또 1장의 가격은 1,000원이다.
* 당첨 번호와 보너스 번호를 입력받는다.
* 사용자가 구매한 로또 번호와 당첨 번호를 비교하여 당첨 내역 및 수익률을 출력하고 로또 게임을 종료한다.
* 사용자가 잘못된 값을 입력할 경우 IllegalArgumentException를 발생시키고, "[ERROR]"로 시작하는 에러 메시지를 출력 후 종료한다.



## 입출력 요구 사항


# 입력

* 어떤 로또를 구입할 지 입력받는다. 작은 로또의 경우 1, 중간 로또의 경우 2, 큰 로또의 경우 3을 입력한다. 이외의 숫자가 입력되면 예외 처리한다.
2
* 로또 구입 금액을 입력 받는다. 구입 금액은 1,000원 단위로 입력 받으며 1,000원으로 나누어 떨어지지 않는 경우 예외 처리한다.
14000
* 당첨 번호를 입력 받는다. 번호는 쉼표(,)를 기준으로 구분한다.
1,2,3,4,5,6
* 보너스 번호를 입력 받는다.
7


# 출력

* 발행한 로또 수량 및 번호를 출력한다. 로또 번호는 오름차순으로 정렬하여 보여준다.

8개를 구매했습니다.
[8, 21, 23, 41, 42, 43] 
[3, 5, 11, 16, 32, 38] 
[7, 11, 16, 35, 36, 44] 
[1, 8, 11, 31, 41, 42] 
[13, 14, 16, 38, 42, 45] 
[7, 11, 30, 40, 42, 43] 
[2, 13, 22, 32, 38, 45] 
[1, 3, 5, 14, 22, 45]

* 당첨 내역을 출력한다. 구매한 로또의 당첨 금액에 해당하는 당첨금을 보여준다.

//중간 로또의 경우
3개 일치 (5,000원) - 1개
4개 일치 (50,000원) - 0개
5개 일치 (150,000원) - 0개
5개 일치, 보너스 볼 일치 (3,000,000원) - 0개
6개 일치 (50,000,000원) - 0개
수익률은 소수점 둘째 자리에서 반올림한다. (ex. 100.0%, 51.5%, 1,000,000.0%)
총 수익률은 62.5%입니다.

* 예외 상황 시 에러 문구를 출력해야 한다. 단, 에러 문구는 "[ERROR]"로 시작해야 한다.

[ERROR] 로또 번호는 1부터 45 사이의 숫자여야 합니다.
 


## 프로그램 요구 사항

* 함수(또는 메서드)의 길이가 15라인을 넘어가지 않도록 구현한다.
* 함수(또는 메서드)가 한 가지 일만 잘 하도록 구현한다.
* else 예약어를 쓰지 않는다.
  힌트: if 조건절에서 값을 return하는 방식으로 구현하면 else를 사용하지 않아도 된다.
* 추상화를 적절하게 사용한다.
* MVC 패턴과 도메인을 적절하게 적용하여 구현한다.
* Java Enum을 적용한다.






그리고 나름대로 입력과 출력을 요구 사항 대로 잘 맞추었다.



### 코드


{% highlight Java %}

package org.example;

import java.util.Scanner;

import org.w3c.dom.css.CSS2Properties;

import java.nio.charset.IllegalCharsetNameException;
import java.util.Arrays;
import java.util.Collections;
import java.util.Random;

// 추상화를 적절하게 사용한다. 라는 말이 무엇인지 모르겠습니다. 
// MVC 패턴과 도메인을 적절하게 사용하여 구현하라는 말이 무엇인지 모르겠습니다. 

public class LottoApplication {

    int [][] randomNumbers; 
    int[] winNumbers = new int[7];
    Integer paid; 

    static double value = 0; 

    public int getKindOfLotto() {
        Scanner input = new Scanner(System.in); 
        int kindLotto;

        while (true) {
            try {
                Exception e = new IllegalArgumentException();
                kindLotto = input.nextInt();
                if (kindLotto < 1 || kindLotto > 3) {
                    throw e; 
                }
                break;
            } catch (Exception e) {
                System.out.println("[ERROR] 로또의 종류는 작은 로또(1), 중간 로또(2), 큰 로또(3) 세 가지 뿐입니다. 다시 입력해 주세요:");
            }
        }

        return kindLotto;
    }

    public int getPaid() {       // 로또를 구매하기 위해 지불할 돈을 입력 받는다. 한 장에 1000원 이므로 반드시 금액은 1000으로 나누어 떨어져야 한다. 
        Scanner input = new Scanner(System.in); 
        int paid; 
        while (true) {
            paid = input.nextInt(); 
            try {
                Exception e = new IllegalArgumentException();
                if (paid % 1000 != 0) throw e; 
                return paid;
            } catch (Exception e) {
                System.out.println("[ERROR] 로또 한 장은 1,000원이므로, 지불 금액은 반드시 1000의 배수여야 합니다. 다시 입력 하세요: ");
            }
        }
    }

    public Boolean[] countBonus(int index) {       // 보너스 로또 번호를 따로 입력 받는다.
        Boolean[] bonus = new Boolean[index];
        int i = 0; 
        for (int [] list: randomNumbers) {
            if (Arrays.asList(list).contains(winNumbers[6]))
                bonus[i++] = true; 
        }
        return bonus;
    }

    public void createRandomNumbers(int paid) {      // 로또 번호들을 랜덤하게 생성하여 int 형 배열에 저장한다. 
        randomNumbers = new int[paid/1000][6];       // flag 라는 변수를 사용하면 안될 것 같은데...
        int[] arr = new int[6]; 
        Random random = new Random(); 
        int flag; 
        for (int i = 0; i < paid/1000; i++) {
            for (int j = 0; j < 6; j++) {
                flag = 0; 
                int num = random.nextInt(45) + 1; 
                for (int k = 0; k < j; k++) {
                    if (num == arr[k]) {
                        j--; flag = 1;
                    }
                }
                if (flag == 1) continue;
                arr[j] = num; 
            }
            Arrays.sort(arr); 
            randomNumbers[i] = arr.clone();
        }
    }

    public void showRandomNumbers(int paid) {      // 생성된 로또 번호들을 출력하는 메서드다.  
        for (int i = 0; i < paid/1000; i++) {
            System.out.print("[");
            for (int j = 0; j < 6; j++) {
                System.out.print(Integer.toString(randomNumbers[i][j]));
                if (j != 5) System.out.print(", ");
            }
            System.out.println("]");
        }
    }

    public void getWinNumbers() {      // 당첨 번호를 입력 받는다. 번호는 반드시 1~45 사이여야 한다. 
        Scanner input = new Scanner(System.in); 
        String[] winNumber = input.nextLine().split(",");; 
        for (int i = 0; i < 6; i++) {
            try {
                Exception e = new IllegalArgumentException();
                if (Integer.parseInt(winNumber[i]) < 1 || Integer.parseInt(winNumber[i]) > 45 || winNumber.length < 1 || winNumber.length > 6) {
                    throw e;
                }
            } catch (Exception e) {
                System.out.println("[ERROR] 로또 번호는 1부터 45 사이의 6개의 숫자여야 합니다.");
                winNumber = input.nextLine().split(",");
                i = 0; continue; 
            } 
            winNumbers[i] = Integer.parseInt(winNumber[i]); 
        }
    }

    public void getBonusNumber() {      // 보너스 번호를 따로 입력 받는다. '5개 일치 + 보너스 일치' 라는 조건 때문에 따로 저장한다. 
        Scanner input = new Scanner(System.in); 
        int bonus;
        while (true) {
            try {
                Exception e = new IllegalArgumentException();
                bonus = input.nextInt(); 
                if (bonus < 1 || bonus > 45) throw e;
                break;
            } catch (Exception e) {
                System.out.println("[Error] 로또 번호는 1부터 45 사이의 숫자여야 합니다.");
            }
        }
        winNumbers[6] = bonus; 
    }

    public int[] howManyWins(int index) {      // 당첨 번호의 개수를 세는 메서드다. 
        int howMany; 
        int[] result = new int[index]; 
        int i = 0; 
        for (int[] list: randomNumbers) {
            howMany = 0; 
            for (int number: list) {
                for (int j = 0; j < 7; j++) {
                    if (winNumbers[j] == number) {
                        howMany++; 
                    }
                }
            }
            result[i++] = howMany; 
        }
        return result;
    }

    public String[] moneyEachPrize(int kindLotto) {      // 작은 로또, 중간 로또, 큰 로또에 따라 달라지는 당첨액을 표현하는 메서드다. 
        String[] money = new String[5];
        switch (kindLotto) {
            case 1: 
                money[0] = "2,000,000"; money[1] = "30,000"; money[2] = "1,500"; 
                money[3] = "500"; money[4] = "100"; 
                break;
            case 2: 
                money[0] = "50,000,000"; money[1] = "3,000,000"; money[2] = "150,000"; 
                money[3] = "50,000"; money[4] = "5,000"; 
                break;
            case 3:
                money[0] = "2,147,000,000"; money[1] = "850,000"; money[2] = "10,000"; 
                money[3] = "0"; money[4] = "0"; 
                break;
        }

        return money; 
    }

   
    public String toString(String[] moneyPrize, int[] result, Boolean[] hasBonus) {     // 당첨 결과를 출력하는 toString 메서드다. 왜 @override 메서드를 사용하지 않아도 될까?
        int first=0, second=0, third=0, fourth=0, fifth=0;
    
        for (int i = 0; i < result.length; i++) {
            if (result[i] == 3) first++; 
            if (result[i] == 4) second++;
            if (result[i] == 5) {
                if (hasBonus[i] == true) fourth++;  
                else third++; 
            }
            if (result[i] == 6) fifth++;
        }

        value = first * Integer.parseInt(moneyPrize[4].replace(",", ""))      // 수익률을 여기서 계산한다. 
        + second * Integer.parseInt(moneyPrize[3].replace(",", ""))
        + third * Integer.parseInt(moneyPrize[2].replace(",", ""))
        + fourth * Integer.parseInt(moneyPrize[1].replace(",", ""))
        + fifth * Integer.parseInt(moneyPrize[0].replace(",", ""));

        return "3개 일치 (" + moneyPrize[4] + "원) - " + Integer.toString(first) + "개\n"
        + "4개 일치 (" + moneyPrize[3] + "원) - " + Integer.toString(second) + "개\n"
        + "5개 일치 (" + moneyPrize[2] + "원) - " + Integer.toString(third) + "개\n"
        + "5개 일치, 보너스 볼 일치 (" + moneyPrize[1] + "원) - " + Integer.toString(fourth) + "개\n"
        + "6개 일치 (" + moneyPrize[0] + "원) - " + Integer.toString(fifth) + "개\n";
    }
    
    // 구현할 기능
    // 1. 숫자를 랜덤 생성할 때 중복된 수들이 없어야 함.  ==> 해결됨. (더욱 멋진 코드로 바꾸는 작업이 필요할 듯)
    // 2. 예외 상황 시 에러 문구를 출력해야 한다. 단, 에러 문구는 "[ERROR]"로 시작해야 한다. => 해결됨. 
    // ** 가능한 예외 상황:
    //  - 로또 번호를 1~45 사이의 정수가 아닌 수를 입력 받았을 때. ==> 해결됨. 
    //  - 낸 돈이 1000으로 나누어 떨어지지 않을 때. ==> 해결됨. 
    //  - 입력된 당첨 번호의 개수가 1보다 작거나 6보다 클 때. ==> 해결됨. 
    //  - 로또 종류를 입력 받을 때 1, 2, 3 가 아닌 다른 수를 입력 받을 때. ==> 해결됨. 
    // 3. Java Enum을 적용한다. 
    //  - Enum 자료구조에 대한 공부가 더 필요할 듯... 어떻게 사용해야 하지. 어떤 기능에 적용해야 할까?


    public static void main(String[] args) {   // main 함수에서 static 을 없애도 되나? 이걸 없애야 main 밖에 있는 변수들을 가져다 쓸 수 있는디. 
        
        java.util.Scanner input = new Scanner(System.in);
        LottoApplication lottoApplication = new LottoApplication(); 

        System.out.println("구입할 로또 종류를 선택해주세요. (작은 로또: 1, 중간 로또: 2, 큰 로또: 3)");
        int kindLotto = lottoApplication.getKindOfLotto(); 

        System.out.println("구입금액을 입력해 주세요."); 
        int paid = lottoApplication.getPaid(); 

        System.out.println(Integer.toString(paid/1000) + "개를 구매했습니다.");
        lottoApplication.createRandomNumbers(paid);
        lottoApplication.showRandomNumbers(paid);

        System.out.println("당첨 번호를 입력해 주세요:");
        lottoApplication.getWinNumbers();

        System.out.println("보너스 번호를 입력해 주세요:");
        // winNumbers[6] = bonus;        // 이거 왜 안되는 거지?   
        lottoApplication.getBonusNumber(); 

        int[] result = lottoApplication.howManyWins(paid/1000).clone();
        Boolean[] hasBonus = lottoApplication.countBonus(paid/1000).clone(); 
        String[] moneyPrize = lottoApplication.moneyEachPrize(kindLotto).clone(); 

        System.out.println("당첨 통계\n---");
        System.out.println(lottoApplication.toString(moneyPrize, result, hasBonus)); 

        double percentage = value / paid * 100; 
        System.out.println("총 수익률은 " + String.format("%.1f", percentage) + "%입니다. ");
    }
}

{% endhighlight %}





## 추상화를 적절하게 사용한다

`추상화`가 도대체 뭘까? 해당 용어는 귀에 익은데, 정확한 의미가 뭘까?

위키백과에 `추상화(컴퓨터과학)`을 검색하면, "컴퓨터 과학에서 추상화(abstraction)는 복잡한 자료, 모듈, 시스템 등으로부터 핵심적인 개념 또는 기능을 간추려 내는 것을 말한다." 라고 되어 있는 것을 볼 수 있다.
코드로 추상화를 구현한다는 것은, 구체적으로 무엇을 말하는 걸까?



## MVC 패턴과 도메인을 적절하게 적용하여 구현한다. 

`MVC 패턴`과 관련된 자료들을 몇 번 읽은 적이 있다. 자료를 여러번 읽어도 이해가 잘 되지 않는 것으로 보아, 직접 코드를 여러번 구현해 보는 등 경험이 쌓여야만 이해할 수 있을 부분인 것 같다. 
`도메인`을 적절하게 적용하라는 얘기도... 사실 모르겠다. 


## 예외 사항 처리하기

예외 사항은 모두 try-catch 문으로 처리하도록 노력했다. 실은, while 문이나 if 문만으로도 충분히 처리할 수 있을 것 같았지만, try-catch 문에 익숙해질 필요가 있다고 느껴, 이번 과제에서는 최대한 이 구문을 사용하도록 노력하였다. 

## Java Enum을 적용한다.

Enum 자료구조를 어디에, 어떻게 사용해야 하나 고민을 해보았지만 아이디어가 떠오르지 않는다.
Enum 자료구조에 대한 이해도나 사용 방법에 대해 더 공부를 해보아야 할 것이고, 이 자료구조를 어떤 기능을 위하여 사용할 수 있을지도 생각해 보아야할 일이다. 

![enum1](/assets/images/banners/2023-03-05/enum1.jpg)
![enum2](/assets/images/banners/2023-03-05/enum2.jpg)
![enum3](/assets/images/banners/2023-03-05/enum3.jpg)
![enum4](/assets/images/banners/2023-03-05/enum4.jpg)
![enum5](/assets/images/banners/2023-03-05/enum5.jpg)
![enum6](/assets/images/banners/2023-03-05/enum6.jpg)
![enum7](/assets/images/banners/2023-03-05/enum7.jpg)
![enum8](/assets/images/banners/2023-03-05/enum8.jpg)
![enum9](/assets/images/banners/2023-03-05/enum9.jpg)
![enum10](/assets/images/banners/2023-03-05/enum10.jpg)


## Enum 클래스를 이렇게 바꿔보면 어떨까?

{% highlight Java %}

enum Prize {
    FIRST_PRIZE("2,000,000", "50,000,000", "2,147,000,000"), 
    SECOND_PRIZE("30,000", "3,000,000", "850,000"), 
    THIRD_PRIZE("1,500", "150,000", "10,000"), 
    FOURTH_PRIZE("500", "50,000", "0"), 
    FIFTH_PRIZE("100", "5,000", "0"),
    WON("원) -"),
    GAE("개\n");

    final private String small; 
    final private String middle;
    final private String big;
    public String getName() {
        return small; 
    }
    private Prize(String small, String middle, String big) {
        this.small = small; 
        this.middle = middle; 
        this.big = big;
    }
}

{% endhighlight %}

그리고 Enum상수를 `Prize.FIRST_PRIZE.big` 이런 식으로 불러올 수 있을 것이다. 

### Controller, Service, Repository

![spring1](/assets/images/banners/2023-03-05/spring1.jpg)
![spring2](/assets/images/banners/2023-03-05/spring2.jpg)
![spring3](/assets/images/banners/2023-03-05/spring3.jpg)
![spring4](/assets/images/banners/2023-03-05/spring4.jpg)
![spring5](/assets/images/banners/2023-03-05/spring5.jpg)
![spring6](/assets/images/banners/2023-03-05/spring6.jpg)
![spring7](/assets/images/banners/2023-03-05/spring7.jpg)

## 궁금한 점

왜 main 함수의 예약어 중에서 static 을 빼면 안될까? static 을 빼면, main 함수 밖에 선언한 변수나 자료구조들을 자유롭게 끌어다 쓸 수 있을 것 같은데 말이다. 



### 여기까지의 평가

Java 를 배워본 적이 없기 때문에, 더욱 쉽게 작성할 수 있었을 코드를 어렵게 작성한 것 같은 기분이 없지 않아 든다. 더욱 쉽고 간편한 라이브러리들이 있을 텐데, 해당 라이브러리들을 모르니 다중 for 문을 사용하는 등 비효율적인 코드가 많이 생성 되었을 것이라고 예상한다. 이 뿐만 아니라 '객체지향적'인 코드가 아닐 가능성이 매우 클 것이다. 애초에 객체지향적으로 코딩을 해본 적이 많이 없기 때문이다.
Java Enum 자료 구조를 사용하여야 하는데, Enum 자료구조가 익숙하지 않은 바람에 어떤 부분에서 써야할지부터 감이 안 온다. 


위와 같은 문제들을 스터디 멤버들과 함께 나누고 고쳐나가면서 나의 실력이 쑥쑥 늘었으면 좋겠다.
2023년 12월에 여러 프로그램들을 자유자재로 만들어 나가는 나의 모습을 상상하면 설렌다.