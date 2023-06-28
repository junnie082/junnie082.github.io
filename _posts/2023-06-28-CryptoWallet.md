---
layout: post
title: STCE 암호동아리 암호 공모전 준비 1주차
subtitle: 암호화폐 지갑
author: Jun
categories: security
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
tags: cipher
sidebar: []
---

# 2023.06.28.(수)

### 국가 암호 공모전 주제 및 일정

## 암호화폐 지갑 패스워드 복구 매커니즘 분석

- 패스워드 복구

* 필요성:

1. 비정형파일(.hwp, .docx, .pdf, .zip 등), 암호화 앱, 암호지갑 등에서 제공하는 암호기술이 범죄 증거를 은닉하는 데 활용되어, 실체적 진실 발견과 범죄수익 환수에 막대한 지장을 초래하고 있음.
2. 이에 따라, 법집행기관의 영장 집행 시 피압수자 협조여부와 상관 없이 범죄 단서를 확보하기 위한 기법 연구가 절실히 필요.

- 패스워드 크래킹 (Password Cracking 기법):

1. Dictionary Attack(사전 대입 공격): 흔히 쓰이는 패스워드들을 모두 저장하여 대입해 보는 방식의 공격. 패스워드가 해당 사전에 저장되어 있지 않으면 실패.
2. Brute Force Attack(무작위 대입 공격): 조합 가능한 모든 패스워드를 대입해보는 공격 (0-9, a-z, 특수문자 등을 조합하여 무작위로 대입/ 모든 경우의 수를 수행하여 100%의 성공률을 가지지만, 패스워드가 길다면 천문학적인 시간이 걸릴 수 있음.)

- 대표적인 도구: Hashcat  
  [hashcat](https://hashcat.net/hashcat/)

* 무료 도구 중 가장 성능이 뛰어나고, 지원 포맷이 다양함.

## Bither

Bither는 모바일과 웹에서 모두 동작하며 다양한 플랫폼에서 서비스를 지원하는 오픈소스 비트코인 암호지갑이다. 휴대폰이나 컴퓨터에 Bither를 설치하면 자동으로 초기 주소가 생성되고 이후 사용시 수동으로 주소를 생성하여 사용한다.
모든 주소는 일회용이며 거래 상대와 지갑 주소를 공유함으로써 거래가 진행된다. 비트코인 거래는 기본적으로 블록체인 네트워크를 사용해 이루어지며 이때 타원곡선 알고리즘 기반으로 공개키쌍을 사용한다.  
Bither의 암호해독 및 검증 프로세스는 다음과 같다.

![Bither 암호해독 메커니즘 전체 개요](/assets/images/banners/2023-06-28/Bither.png)

# 파일 전처리 및 데이터 수집

Bither 암호지갑에서 사용되는 개인키를 복호화하기 위해서는 키 유도 과정에 사용되는 salt 값과 사용자가 설정한 passward, 암호화 된 개인키 (Encrypted private key),
그리고 개인키 복호화 과정에 사용되는 IV 값이 필요하다. 사용자의 PC에 Bither 앱이 설치되면

![디렉토리](/assets/images/banners/2023-06-28/Directory.png)

와 같이 C:\User\사용자\AppData\Roaming\Bither 폴더가 생성되고, 이 폴더 내에 앱 실행과 관련된 데이터들이 저장된다. 이때 AppData 파일은 숨김 파일로 윈도우 파일 탐색기에서 숨김 파일 보기 설정을 해주어야 확인 가능하다.

개인키 복호화 과정에서 사용되는 encrypted private key, iv, salt 값과 복호화한 개인키 검증과정에서 사용되는 사용자 공개키는 위에서 확인 가능한 address 데이터베이스 파일에서 찾을 수 있다.  
해당 데이터베이스 파일에서 파싱해야 하는 값은 address 테이블의 encrypted_private_key 값과 pub_key 값이다. 새로운 거래를 하기 위해 새 지갑 주소를 생성할 때마다 행(address)이 추가된다.

![데이터베이스](/assets/images/banners/2023-06-28/Database.png)

[표16]은 현재 address.db 파일 address 테이블의 첫 번째 행에 존재하는 지갑 주소 데이터이다. 암호 해독을 위해 필요한 데이터는 encrypt_private_key 열과 pub_key 열이다. encrypt_private_key 열에는 사용자의 암호화된 개인키, IV 값,
salt 값이 각각 슬래시(/)로 구분되어 저장되며 pub_key 열에는 base58 인코딩 된 사용자의 공개키가 저장된다. DB 파일에 저장된 데이터를 파싱하기 위해 Sqlite3 라이브러리를 사용하며, Sqlite3 라이브러리는 "http://www.sqlite.org/download.html" 에서
"sqlite-amalgamation-3390200.zip" 파일을 다운로드한 후 C 프로젝트에 추가하여 사용할 수 있다. encrypt_public_key 열에는 encrypted private key, IV, salt 세 값이 함께 저장되어 있으므로 데이터 파싱 후에
슬래시(/)를 기준으로 데이터를 분리하는 작업이 필요하다. 슬래시(/) 기준 맨 앞 96글자(48bytes)가 encrypted private key, 가운데 32글자(16bytes)가 IV, 마지막 16글자(8bytes)가 salt 값이다.
마지막으로, encrypt_private_key 열에 저장된 데이터는 16진수(hex) 형식이지만 데이터 추출 과정에서 각 4bit가 하나의 character로 인식되기 때문에 추출한 전체 string을 byte 단위로 바꿔주는 작업이 필요하다.  
Bither 암호해독 과정에 필요한 데이터의 기본 경로는 "C:\User\사용자\AppData\Roaming\Bither\address.db"이고 각 데이터 별 세부 정보는 [표 17]과 같으며 전체 데이터 수집 과정은 다음과 같다.

![데이터](/assets/images/banners/2023-06-28/Data.png)  
![데이터2](/assets/images/banners/2023-06-28/Data2.png)

# 키 유도 과정 (패스워드 이용)

사용자의 개인키가 암호화되는 프로세스트는 다음 그림과 같은데, 이중 파란색으로 표시된 encrypted private key, iv, salt 값은 Bither 앱 설치 시 생성되는 address.db 파일에서 확인 가능하다.

![개인키](/assets/images/banners/2023-06-28/PersonalKey.png)

### 암호화폐 지갑이란?

[암호화폐 지갑이란?](https://www.heybit.io/insight/article/what-are-cryptocurrency-wallets)

`내가 가고 있는 암호화폐`는 참여자 모두가 공유하는 블록체인 네트워크상에 존재합니다.
실제 암호화폐 지갑에는 암호화폐가 들어있진 않으나, 블록체인 네트워크상에서 저 암호화폐는 '내 것'이고 기록되어 있고, 그 기록을 인증하기 위한 키(key)를 관리하는 도구가 바로 암호화폐 지갑입니다.
이를 `개인키` 라고 하는데요.

지갑에서 관리하는 개인키를 잃어버리면 암호화폐가 사라지는 것이 아니라 내 암호화폐의 소유권을 증명할 수 없게 되는 것입니다.
암호화폐 자산 관리에서 가장 중요한 일 중 하나가 바로 `개인키를 철저하게 관리`하는 것입니다.

### 소유권에 따른 지갑의 분류

암호화폐 지갑은 소유권과 인터넷 연결 유무에 따라 구분할 수 있습니다.

소유권은 암호화폐 지갑의 개인키를 의미하는데, 암호화폐 지갑은 이 개인키를 내가 관리하느냐, 혹은 남이 관리해 주느냐에 따라서도 구분할 수 있습니다.
개인키를 직접 관리하는 지갑을 비수탁형 (Non-custodial) 지갑이라고 하고, 개인키를 남이 관리해주는 것이 바로 수탁형(custodial) 지갑이라고 합니다.

`거래소에서 제공하는 계좌의 형태를 수탁형 지갑`이라고 합니다.
반면 `비수탁형 지갑은 개인키를 사용자 본인이 직접 관리`하기 때문에 수탁형 지갑에 비해 안전할 수 있습니다.

### 인터넷 연결 유무에 따른 지갑의 분류

- 콜드 월렛
- 핫 월렛  
  두 가지를 나누는 기준은 인터넷 연결 유무인데,  
  `핫 월렛`은 인터넷 주소가 네트워크에 연결되어 있어 온라인 상태에서만 거래를 주고 받을 수 있습니다.  
  `콜드 월렛`은 온라인에 연결되어 있지 않고, 오프라인 상태에 있으므로 거래가 아예 안되어 오프라인 지갑이라고 부르기도 한다.

* 콜드 월렛(Cold Wallet): 인터넷이 차단된 하드웨어 장치에 암호화폐를 보관하며, 상대적으로 보안이 뛰어난 지갑 ex) 디센트, 나노렛저
* 핫 월렛(Hot Wallet): 인터넷에 연결되어 있어 온라인으로 빠르고 암호화폐를 주고받을 수 있는 소프트웨어 지갑 ex) 메타마스크, 카이카스

[Hashcat tutorial for beginners](https://resources.infosecinstitute.com/topic/hashcat-tutorial-beginners/)  
[passware](https://www.passware.com/training/)
