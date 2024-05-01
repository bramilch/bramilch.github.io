---
layout: post
title: "리눅스 배포판과 CentOS, 우분투 비교"
author: bramilch
date: 2024-04-29 18:00:00 +0900
categories: [Backend, Data Engineering]
tags: [Backend, Data Engineering]
pin: true
math: true
toc: true
comments: false
mermaid:
  false
  # alt: Responsive rendering of Chirpy theme on multiple devices.
image:
  path: ./assets/img/posts/2024-04-29-linux-distro/linux-distro.png
---

<br>

> 2024/04/29: 초안 작성
 
※ 내용에 오류가 있을 수 있습니다.

<br>

**목차**

- [리눅스 배포판 Linux Distribution (Distro)](#리눅스-배포판-linux-distribution-distro)
- [레드햇 리눅스 계열과 데비안 리눅스 계열 비교](#레드햇-리눅스-계열과-데비안-리눅스-계열-비교)
- [센트OS CentOS와 우분투 Ubuntu 비교](#센트os-centos와-우분투-ubuntu-비교)
- [CentOS 프로젝트와 Red Hat의 결정](#centos-프로젝트와-red-hat의-결정)
  - [CentOS 프로젝트는 누가, 왜 시작했고, CentOS 7, 8는 왜 종료 결정이 되었을까](#centos-프로젝트는-누가-왜-시작했고-centos-7-8는-왜-종료-결정이-되었을까)
- [참고자료](#참고자료)

<br>

## 리눅스 배포판 Linux Distribution (Distro)

<br>

<center><span style="font-size:1.2em;">많은 종류의 리눅스 배포판</span></center>

<br>

![linux distro](/assets/img/posts/2024-04-29-linux-distro/linux-distro.png)


<br>

- 흔히들 리눅스 배포판이라고 하는데 그런 다른 판도 있을까?

  → 다른 '판'이 있는 것이 아니라 Linux는 오픈소스 커널이기 때문에 이를 사용하는 모든 운영 체제를 "Linux 배포판"이라고 하는 것.

- "배포 Distribution"는 Linux 기반 OS를 다른 사용자와 오픈소스로서 공유하는 과정에서 유래되었고, Linux 커널과 OS가 일반적으로 무료이기 때문에 "배포"라고도 함.

- 리눅스 배포판 종류는 크게 9가지  
  
1. 레드햇 계열
2. 맨드리바/마제야 계열
3. 데비안 계열  
   - 3.1. 우분투 계열
4. 아치 계열
5. 슬랙웨어 계열
6. 젠투 계열
7. SUSE 계열
8. 안드로이드 계열
9. 기타 배포판

<br>

## 레드햇 리눅스 계열과 데비안 리눅스 계열 비교

<br>

레드햇 계열과 데비안 계열의 차이를 알아보고, 레드햇 계열의 CentOS와 데비안 계열의 Ubuntu를 비교하겠음.

<br>

<center><span style="font-size:1.2em;">레드햇 리눅스 계열과 데이안 리눅스 비교</span></center>

<br>

| 기능 | 레드햇 리눅스 | 데비안 리눅스 |
|------|-----------------------|-----------------------|
| 기원과 관리 | Red Hat에서 개발, 현재 IBM에서 유지관리 | 자원봉사자가 개발하고 Debian에서 관리함|
| 패키지 관리자명 | RPM(YUM/DNF) | APT(고급 패키지 도구) |
| 출시 주기 | 일반적으로 속도가 느리고 안정성에 중점을 둡니다(RHEL) | 최신 패키지로 더욱 빨라진 릴리스 주기 |
| 안정성 | 안정성과 기업용 사용 강조 | 안정성과 업데이트 사이의 균형 수용|
| 타겟 소비자 | 기업, 서버, 클라우드 인프라 | 서버, 데스크탑, 임베디드를 포함한 광범위|
| 지원 | 구독을 통해 상업적 지원 가능| 활발한 포럼과 IRC를 통한 커뮤니티 지원 |
| 기본 데스크탑 | GNOME(다른 옵션 사용 가능) | GNOME(다른 옵션 사용 가능) |
| 구성 | 서비스 관리를 위해 systemd 사용 | 서비스 관리를 위해 systemd 사용 |
| 시스템 init 역할 프로세스 | systemd  |
| 라이센스 | 독점(오픈 소스 구성 요소 포함) | 무료 및 오픈 소스(GNU GPL) |
| 보안 | 보안 기능 및 업데이트에 대한 강조 | 정기적인 업데이트로 보안 강조 |

<br>

## 센트OS CentOS와 우분투 Ubuntu 비교

- 윈도우에서 WSL2를 설치하면 자동으로 C 드라이브에 Ubunt가 설치됨.

- 데비안 기반 Ubuntu는 개발 환경에 적합하고 레드햇 Red Hat기반 CentOS는 운영 환경에 적합하다고 함.

- 왜? 
  - CentOS와 Ubuntu는 모두 운영, 개발 등 다양한 목적으로 사용될 수 있음. - 운영 환경에선 사용성이 운영에 맞춰져 있고, 보안, 안정성, 장기 지원 측면에서 강점인 CentOS가 선호된 것.
  - 개발 환경에선 사용 편의성, 최신 버전 접근성, 커뮤니티 지원에서 강점인 Ubuntu가 선호된 것.

<br>

<center><span style="font-size:1.2em;">CentOS와 Ubutu 비교</span></center>

<br>

| 기능 | CentOS 센트OS | Ubuntu 우분투 |
|------------|---------------------|------------------|
| 안정성과 신뢰성| 안정성과 장기적인 지원으로 유명함 | 커뮤니티 지원으로 안정성 제공 |
| 보안 중점 | 보안 기능 및 업데이트 강조 | 정기적인 업데이트로 보안에 중점 |
| 기업 지원 | 상용 지원 옵션 제공 | 강력한 커뮤니티 지원 |
| 호환성 | 엔터프라이즈 소프트웨어 호환성 인증 | 풍부한 패키지 생태계 |
| 사용 용이성 | 일반적으로 더 복잡하며 운영에 맞게 맞춤화됨| 사용자 친화적인 인터페이스로 알려져 있음 |
| 최신 소프트웨어 | 느린 릴리스 주기, 이전 소프트웨어 버전 | 최신 소프트웨어로 출시 주기 단축|
| 개발 환경 | 기업 환경에 적합 | 사용 편의성으로 인해 개발 선호|
| 기본 데스크탑 | 일반적으로 기본적으로 데스크탑 환경은 없습니다 | 사용자 편의성을 위해 기본적으로 GNOME 사용|
| 패키지 관리 | RPM 기반(YUM/DNF) | APT(고급 패키지 도구) |
| 라이센스 | 무료 및 오픈 소스(GPL) | 무료 및 오픈 소스(GPL) |


## CentOS 프로젝트와 Red Hat의 결정

<br>

- 2020년, Red Hat에서 현재도 많이 사용하고 있는 CentOS 7, 8 업데이트 중단을 선언

  - CentOS 프로젝트는 Red Hat과 협력하여 향후 Red Hat Enterprise Linux 릴리스를 위한 업스트림 개발 플랫폼인 CentOS Stream에 모두 투자할 것이라고 발표
  
  - 결과적으로 CentOS Linux 7은 2024년 6월 30일에 수명 종료(EOL, End of Life)되고, 업데이트 릴리스가 중단됨. 
  
  - CentOS Linux 8는 2021년 12월 31일에 중단됨.

<br>

### CentOS 프로젝트는 누가, 왜 시작했고, CentOS 7, 8는 왜 종료 결정이 되었을까
--------------------------------------------------------

<br>

  - CentOS 프로젝트는 2004년 Lance Davis에 의해 시작

  - 프로젝트 주된 동기는 Lance Davis와 다른 기여자들은 커뮤니티에서 자유롭게 배포하고 지원할 수 있는 RHEL(Red Hat Enterprise Linux)과 호환되는 배포판의 가치를 믿고, RHEL에 대한 커뮤니티 지원의 무료 오픈소스 대안을 제공하고자 했다고 하나 처음부터 Red Hat의 직원들의 도움을 받은 것으로 보아 Red Hat의 비즈니스 전략이 아니었을까 함.
  
  - RHEL(Red Hat Enterprise Linux)은 상용 Linux 배포판이지만 해당 소스 코드는 공개적으로 사용 가능하여 이를 기반으로 만듦.

  - Red Hat Enterprise Linux는 장기적인 지원, 안정성을 제공하지만 공식 지원 및 업데이트에 액세스하려면 구독료가 필요한 상용 배포판임.
  
  - 사실상 CentOS가 RHEL의 소스 코드 기반으로 만들었고, 돈을 지불해야 하지만 돈을 지불하지 않는 Red Hat 상표를 모두 제거한 OS가 되어갔고 Red Hat은 소스코드 접근 허용, 바이너리 호환성, 커뮤니티를 육성, 지원하고 커뮤니티 기반 서비스나 구축된 커뮤니티를 통한 비즈니스 전략이었던 것 같음.

  - CentOS 프로젝트가 CentOS 7 및 CentOS 8의 수명 종료(EOL)를 조기에 선언한 것은 오픈 소스 커뮤니티에서 심각한 논란을 불러일으킴.

  - CentOS 8 EOL은 원래 예정된 2029년이 아닌 2021년 12월 31일로 크게 단축되었고, 이 발표에는 CentOS Stream을 미래 업스트림 개발 지점으로 도입하는 내용도 포함되었기 때문

  - Red Hat의 이러한 결정의 이유는 다양하지만 주로 기본 CentOS 변형인 CentOS Stream으로 Rolling 릴리스 배포판으로, 업데이트에 더 빠르게 접근할 수 있게 하겠다고 하지만, 이는 RHEL의 안정적인 다운스트림 재구축으로서의 CentOS의 전통적인 역할과는 다름.

  - 많은 사람들이 이를 인프라 계획에 심각한 혼란을 초래하는 것으로 보고 대체 솔루션을 모색하게 됨.
  
<br>
<br>

## 참고자료

[Wikipedia] CentOS  
<https://en.wikipedia.org/wiki/CentOS>

[Make Use Of] Why Does Linux Have So Many Distributions? Linux Distros Explained  
<https://www.makeuseof.com/why-so-many-linux-distributions/#:~:text=Linux%20is%20the%20kernel%2C%20and,the%20OS%20are%20generally%20free>

[Red Hat] What to know about CentOS Linux EOL  
<https://www.redhat.com/en/topics/linux/centos-linux-eol#:~:text=Why%20is%20CentOS%20Linux%20going,)%20on%20June%2030%2C%202024>  

[나무위키] Linux/배포판  
<https://namu.wiki/w/Linux/%EB%B0%B0%ED%8F%AC%ED%8C%90#s-2.1>
