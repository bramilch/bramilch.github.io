---
layout: post
title: 유저 모드 User mode vs 커널 모드 Kernel mode
author: bramilch
date: 2024-05-27 18:00:00 +0900
categories: [Backend, Data Engineering]
tags: [Backend, Data Engineering]
pin: true
math: false
toc: true
comments: false
mermaid: false
image:
  path: ./assets/img/posts/2024-06-07-kr-user-kernel-mode/user-mode-kernel-mode.png
---

<br>

> 2024/06/07: 초안 작성  
 
※ 내용에 오류가 있을 수 있습니다.  
※ 내용을 계속 추가, 수정, 보완하고 있습니다.  

<br>

**목차**

- [[#커널 모드와 유저 모드|커널 모드와 유저 모드]]
- [[#3가지 커널 모드|3가지 커널 모드]]
	- [[#3가지 커널 모드#1. Monolithic Kernel|1. Monolithic Kernel]]
	- [[#3가지 커널 모드#2. Microkernels (or Samuel Kernel)|2. Microkernels (or Samuel Kernel)]]
	- [[#3가지 커널 모드#3. Hybrid Kernel|3. Hybrid Kernel]]


<br>

## 커널 모드와 유저 모드

<br>

> **운영 체제는 커널 모드와 유저 모드를 분리하여 유저 애플리케이션이 시스템의 핵심 기능을 직접 방해하지 못하도록 함으로써(격리) 안정성과 보안을 보장**

<br>

**커널 모드 Kernel Mode**

- 모든 리소스에 대한 전체 액세스 권한

- 장치 드라이버 device drivers 및 시스템 호출 system calls과 같은 중요한 작업을 실행

- 오류가 발생하면 전체 시스템에 영향을 미칠 수 있음(재부팅하거나 OS 재설치 필요할 수 있음).

**유저 모드 User Mode**

- 리소스에 대한 제한된 액세스

- 유저 애플리케이션을 실행

- 오류는 애플리케이션 내에서 발생(OS는 계속 실행됨).

<br>

- 커널 모드는 운영 체제에서 가장 신뢰할 수 있는 가장 낮은 수준의 기능이자 소프트웨어와 하드웨어 사이의 중간자 역할

- 커널은 하드웨어와 소프트웨어 간의 통신을 유지하는 것이 주요 임무. ***커널은 BIOS 직후에 사용자가 컴퓨터에 처음 설치하는 소프트웨어***

- 커널 모드에서 크래시가 발생하면 PC 전체가 중단되는 치명적인 결과를 초래

- OS 커널은 설치되는 하드웨어에 따라 다르며, 윈도우의 NT 커널(MS 386에서 처음 사용), 벨 연구소의 유닉스 코드 ae처럼 하드웨어에 유연한 OS(Hardware extraction layer coding)가 있음.

- 소프트웨어가 CPU에 요청을 할 때 커널 CPU에 따라 다르게 처리하는 시스템 호출이 됨.

- ***OS는 커널 모드와 유저 모드의 두 단계로 실행됨.***

- 유저 모드에서는 실행 코드가 ***하드웨어나 참조 메모리에 직접 액세스할 수 없음.***

- 유저 공간 User Space은 커널 공간 Kernel space보다 권한이 낮으며, 코드, 프로세스 데이터, 날짜 등 커널 공간의 하드웨어와 리소스에 직접 접근할 수 없고 ***가상 공간에만 접근할 수 있음***.

- 유저 공간에서 예외가 발생하면 단일 프로세스만 충돌되고 OS는 계속 실행되지만, 커널 공간 문제의 경우 컴퓨터를 재부팅하거나 OS를 다시 설치해야 할 수 있음.

- Win OS에서 프로그램을 실행하면 개인 가상 주소 공간을 주고, 이 공간에선 무언가에 액세스할 수 없음.

- 심지어 일부 주소는 커널 주소 공간용으로 되어 있으며, 커널 주소 공간에는 가상 주소 공간이 하나만 있음.

- 프로그램을 실행하면 유저 공간과 커널 공간 사이를 전환함. 어떤 작업이 실행되는 동안 파일을 열거나 둘을 조합하여 파일을 열 수 있음.

<br>

## 3가지 커널 모드

<br>

### 1. Monolithic Kernel

<br>



<br>

### 2. Microkernels (or Samuel Kernel)

<br>


<br>

### 3. Hybrid Kernel

<br>



<br>
<br>

[참고자료]

[Linkedin] Kernel mode V$ User mode!!  
<https://www.linkedin.com/pulse/kernel-mode-v-user-pallab-sarma/>

[Microsoft Learn] User mode and kernel mode  
<https://learn.microsoft.com/en-us/windows-hardware/drivers/gettingstarted/user-mode-and-kernel-mode>

[GeeksforGeeks] User mode and Kernel mode Switching 
<https://www.geeksforgeeks.org/user-mode-and-kernel-mode-switching/>