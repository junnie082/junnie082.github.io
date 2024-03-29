---
layout: post
title: STCE 암호동아리 암호 공모전 준비 2주차
subtitle: Etherwall 오픈 소스 분석하기
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

# 2023.07.01.(토)

### Etherwall

[Etherwall](https://www.etherwall.com/about/)

## About

Etherwall is a secure open source ethereum wallet for Windows, Mac OS X and Linux operating systems.  
Etherwall supports the [TREZOR ONE](https://trezor.io) hardware wallet for storing keys.

In full node client mode all data is stored on your computer, but you have to download the full (30GB+ and growing) ethereum blockchain. In thin client mode all your account data stays on your computer. A remote ethereum node is used to get latest blockchain information and send signed transaction.

![etherwall](/assets/images/banners/2023-07-01/etherwall.png)

# What is geth?

[Geth란?](https://medium.com/@taehyoung46/1-geth란-10f115bd9213)

> Ethereum is a decentralized platform that runs smart contracts:
> applications that run exactly as programmed without any possibility of  
> downtime, censorship, fraud or third party interference.

- downtime: 정지 시간, 비사용 시간, 고장 시간, 휴양 기간
- censorship: 검열
- fraud: 사기의

이더리움이란 `스마트 계약을 실행할 수 있는 플랫폼`입니다. go, C++, python 등 다양한 언어로 이더리움을 구동할 수 있는 클라이언트가 개발되고 있으며 현재 가장 많이 사용되는 클라이언트가 go 언어로 개발된 go-ethereum (geth) 입니다.

## Other Wallets

Browser wallets introduce many vulnerabilities. These include centralized servers, disgruntled employees, plug-ins, JavaScript ... etc. Each new path can introduce security holes, leaving your data, keys, I.D. and wallet exposed.

- disgruntled: 불만이 있는

### FAQ

## Basics

# What is Etherwall?

Etherwall is the first GUI wallet released for ethereum back in September 2015. Etherwall is a completely 3rd party 100% open source project hosted on github.

# Is Etherwall an ethereum node?

No, Etherwall currently uses geth as the "back-end" node to provide all the ethereum network functionality.

- ethereum node:  
  An Ethereum node is simply any computer running the software needed to connect with the Ethereum network. Nodes connect with one another to send information back and forth to validate transactions and store data about the state of the blockchain.

# How do I update Etherwall?

Only update Etherwall from this website or the official github link! There are known imposters out there!  
To update on Windows, unzip the file contents and copy them over the old install. To update on Max OS X just drag the app over the old one and override. To update on Linux use the package manager.

# Can I use my own instance of geth?

Yes. Etherwall detects if geth is running already and uses the running instance if geth is using the default data directory. If you're running geth using a custom data directory make sure to configure it in the settings panel.

# Can I run Etherwall with parity as the node?

Yes. Make sure to run parity with the -geth option. If you notice a missing account it is probably due to this bug in parity.

[Other questions](https://www.etherwall.com/faq/)

# Help! I tried sending and got an error about address checksum mismatch!

# How can I reconnect to geth if the IPC connection is broken?

# Where are accounts stored?

## Thin client

# What does a thin client mean?

# How are my keys and passwords protected in thin client mode?

# How is my data protected between Etherwall and the remote server?

# Are IP addresses logged on the server?

## Trezor

# How do I import my accounts from TREZOR ONE?

# Help, my TREZOR T device is not detected?

# What is the import offset parameter?

# What does it mean to remove an account?

## Wallet backups

# How do I backup my wallet?

# How do I restore my wallet?

# Help! My wallet backup file disappeared

# What’s an account export? Is it the same as a wallet export/backup?

## Contracts

# What are contracts?

# Does Etherwall support contracts?

# Why is deploying contracts not supported from source?

# How do I add an existing contract for use?

# How do I deploy a new contract?

# How do I watch a cHow do I view the events for a given contract?

# How do I view the events for a given contract?

## Tokens

# What are tokens? What is ERC20?

# Does Etherwall support Tokens/ERC20?

# How do I add a token to Etherwall?

## DAO/ETC hard fork?

# What is your take on the DAO hack?

# Did you agree with the hard fork?

# Do you support Ethereum Classic (ETC)?

# Did you review the DAO code before investing?

## Using Etherwall with Trezor Wallet Ethereum Hardware Wallet

[![Watch the video](https://img.youtube.com/vi/E0Tryfguxd8/0.jpg)](https://youtu.be/E0Tryfguxd8)

---

[![Watch the video](https://img.youtube.com/vi/47avnc3mu_E/0.jpg)](https://youtu.be/47avnc3mu_E)

![etherwall](/assets/images/banners/2023-07-01/etherwall1.png)
![etherwall](/assets/images/banners/2023-07-01/etherwall2.png)
![etherwall](/assets/images/banners/2023-07-01/etherwall3.png)
![etherwall](/assets/images/banners/2023-07-01/etherwall4.png)

### Etherwall 어떻게 사용할까?

[Etherwall 홈페이지](https://www.etherwall.com/downloads/)에 들어가서 다운을 받으면  
![icon](/assets/images/banners/2023-07-01/icon.png)  
Etherwall이 다운로드 됩니다.

![usage1](/assets/images/banners/2023-07-01/usage1.png)

New accunt 로 새 지갑(?)을 만듭니다.

![usage2](/assets/images/banners/2023-07-01/usage2.png)

id 는 따로 없고... password 만 입력할 수 있게 되어 있습니다!

![usage3](/assets/images/banners/2023-07-01/usage3.png)

이렇게 내가 만든 지갑(?)을 확인할 수 있구요.

![usage4](/assets/images/banners/2023-07-01/usage4.png)

Settings 에 들어가면, `Geth Data Directory`에서 Ethereum의 경로를 확인할 수 있습니다.

![usage5](/assets/images/banners/2023-07-01/usage5.png)

이 수상한 경로를 찾아 들어가 보기로 합니다.

![usage6](/assets/images/banners/2023-07-01/usage6.png)

`keystore` 라는 더 수상한 폴더가 있습니다. 이 폴더 안에 수상한 이름들의 문서들이 있는 것을 확인할 수 있습니다.
새로운 지갑(?)을 만들 때마다 생기는 문서들입니다.

![usage7](/assets/images/banners/2023-07-01/usage7.png)

방금 만든 지갑(?)의 문서에 들어가 보면!!

`address`, `crypto`, `iv` 등등... 기초 세미나 시간에 들어 보았던 단어들이 왕창 나옵니다.

특히 `crypto` 에서 `cipher`를 보면, `aes-128-ctr` 암호 알고리즘 ? 운용 모드 ? 를 사용했음을 알 수 있습니다. (소스 코드에서 보았을 때는, 현수 언니께서 주셨던 검색 [추천 용어들](https://three-fig-f58.notion.site/4c4b847a302040119748bf58e499cdcf)을 모두 쳐보아도 아무것도 안나왔었는데... 여기에 모두 있었군요!)

![code1](/assets/images/banners/2023-07-01/code1.png)

소스 코드는, 우리가 맨 처음에 눌렀던 버튼인 `new account`에서 시작합니다.

![code2](/assets/images/banners/2023-07-01/code2.png)
![code3](/assets/images/banners/2023-07-01/code3.png)

아까부터 계속 눈에 띄던 NodeIPC 는 도대체 뭘까요??

아무리 찾아도 원형 함수가 보이지 않습니다.

혹시나 하여 인터넷에 검색해 보았더니, npm, 즉 node.js 와 관련된 외부 라이브러리 같습니다.  
![nodeIPC](/assets/images/banners/2023-07-01/nodeIPC.png)

### 이번주는 여기까지!!
