---
layout: post
title: "리눅스 역사와 핀토스, 시뮬레이터와 에뮬레이터 차이"
author: bramilch
date: 2024-04-22 18:00:00 +0900
categories: [Backend, Data Engineering]
tags: [Backend, Data Engineering]
pin: true
math: true
toc: true
comments: false
mermaid:
  false
  # alt: Responsive rendering of Chirpy theme on multiple devices.
---

<br>

> 2024/04/22: 초안 작성

※ 내용에 오류가 있을 수 있습니다.

<br>

**목차**

- [리눅스 역사 Linux History](#리눅스-역사-linux-history)
- [Pintos 핀토스 ~~핀트 OS~~](#pintos-핀토스-핀트-os)
- [참고자료](#참고자료)

<br>

## 리눅스 역사 Linux History

- 동시대 여러 개발 프로젝트들이 혼합되고 영향을 주어 탄생

_1969년 Ken Thompson과 Denis Ritchie가 UNIX 운영체제 개발 시작하여 1971년 Bell Labs 내부적으로 어셈블리어로 유닉스 OS 배포(Publishing)_

_→ CPU 제조사마다 다르게 어셈블리어를 다시 짜야함._

_→ Denis Ritchie가 이식성 좋은 UNIX로 만들기 위해 C언어 개발(1972년) 후 UNIX를 C언어로 다시 짬(UNIX 3세대)_

_→ 벨 랩스가 유닉스를 대학, 연구소에만 무료 개방(일반 사용자와 회사들은 유료)_

_→ 1980년대 리처드 스톨먼이 유닉스 완전 오픈을 위해 MINIX 운영체제 GNU 프로젝트 시작했으나 진도 지지부진. 그러나 학부 연습용 OS로 많이 사용_

_→ 헬싱키 대학 리누스 토발즈가 MINIX 운영체제 마음에 안 들어 Linux 커널 개발 개인 프로젝트로 시작했다가 혼자 개발 어렵고, 공개할 계획이라 GNU 프로젝트 이어받아 소스코드 공개하면서 전세계 가장 큰 오픈소스 프로젝트가 됨._

> 1991년 9월 17일 첫 리눅스 배포(Release, 리누스 토발즈 나이 22세.....!! 학부생??!!!)

<br>

- 리눅스재단 Linux Foundation의 큰 프로젝트들

1. 제일 큰 프로젝트가 Linux Kernel 개발
2. 2번째가 Pytorch 라이브러리
   - Pytorch는 페북이 만들었다가 메타가 AI하면서 한계
   - Pytorch는 애초에 오픈 방향성이었기 때문에 디펜던시 가지는 것보다 리눅스 재단에 넘김으로써 오픈소스 라이브러리가 됨.

<br>

## Pintos 핀토스 ~~핀트 OS~~

- 2004년 스탠포드 대학에서 컴퓨터 공학과 수업을 위해 Ben Pfaff가 처음 만든 교육용 가벼운 OS, 미니 OS로 개발한 Pintos
- OS 시뮬레이터 OS Simulator, 운영체제 프레임워크인 소프트웨어 Pintos는 OS 공부하기 위한 OS. 현재도 전세계 모든 대학들이 OS 공부할 때 사용 ~~Pintos 전에 MINIX가 있었다~~
- Pintos Project는 총 4단계로 나누어져 있으며, 각 단계 별로 OS의 필수 구현 사항들을 완성하게 된다. ~~해보고싶다~~

<br>

> **_에뮬레이터 Emulator와 시뮬레이터 Simulator의 차이_**
>
> - 에뮬레이터는 현재 사용하고 있는 시스템, 장치를 대체하는 것을 말하고, 시뮬레이터는 가설 연구, 테스트, 학습을 위한 이론적 모델, 시스템, 장치이다.
>
> - 에뮬레이터의 원형인 Emulate의 뜻은 Imitate. 1963년 IBM 엔지니어들이 시뮬레이션 프로세스의 속도를 높이기 위해 마이크로코드가 처음 사용되었을 때 이 개념을 설명하기 위해 "에뮬레이터"라는 용어를 만들었음.
> - 2000년대에는 소프트웨어 맥락에서 '에뮬레이트'라는 단어를 사용하는 것이 일반화되었음.
>   > [위키피디아 에뮬레이터 Wikipedia Emulator](https://en.wikipedia.org/wiki/Emulator#:~:text=In%201963%2C%20when%20microcode%20was,in%20the%20context%20of%20software.)  
>   > "In 1963, when microcode was first used to speed up this simulation process, IBM engineers coined the term "emulator" to describe the concept. In the 2000s, it has become common to use the word "emulate" in the context of software."
>
> [stackoverflow의 답변](https://stackoverflow.com/questions/1584617/simulator-or-emulator-what-is-the-difference)  
> "An emulator is an alternative to the real system but a simulator is used to optimize, understand and estimate the real system."  
> 에뮬레이터는 실제 시스템의 대안이지만 시뮬레이터는 실제 시스템을 최적화하고 이해하고 추정하는 데 사용됩니다.
>
> [Avenga의 Emulator vs.
> simulator article](https://www.avenga.com/magazine/emulator-vs-simulator/#:~:text=An%20emulator%20replaces%20the%20device,real%20and%20virtual%20devices%20emulator) _자세하게 알고 싶은 분께 추천_  
> "An emulator replaces the device for actual use. A simulator is a theoretical model for research and testing hypotheses."  
> 에뮬레이터는 실제 사용하는 장치를 대체합니다. 시뮬레이터는 가설을 연구하고 테스트하기 위한 이론적 모델입니다.

<br>
<br>

## 참고자료

[Wikipedia] Linux
<https://en.wikipedia.org/wiki/Linux>

[Wikipedia] Linus Torvalds
<https://en.wikipedia.org/wiki/Linus_Torvalds>

[Wikipedia] Unix
<https://en.wikipedia.org/wiki/Unix>

[Wikipedia] C (programming language)
<https://en.wikipedia.org/wiki/C_(programming_language)>

[나무위키] PintOS ~~주로 Pintos라고 부른다~~  
<https://namu.wiki/w/PintOS>

[Wikipedia] Emulator  
<https://en.wikipedia.org/wiki/Emulator#:~:text=In%201963%2C%20when%20microcode%20was,in%20the%20context%20of%20software.>

[Stackoverflow] Simulator or Emulator? What is the difference?
<https://stackoverflow.com/questions/1584617/simulator-or-emulator-what-is-the-difference>

[Avenga] Emulator vs. simulator article  
<https://www.avenga.com/magazine/emulator-vs-simulator/#:~:text=An%20emulator%20replaces%20the%20device,real%20and%20virtual%20devices%20emulator>

[Stanford Univ.] Pintos Projects: Introduction  
<https://web.stanford.edu/class/cs140/projects/pintos/pintos_1.html>
