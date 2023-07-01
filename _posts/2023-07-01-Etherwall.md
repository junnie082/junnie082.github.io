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
