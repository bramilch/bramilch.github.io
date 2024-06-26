---
layout: post
title: "컴퓨팅 4대 리소스 - CPU 구조와 작동 원리"
author: bramilch
date: 2024-05-04 18:00:00 +0900
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
  path: ./assets/img/posts/2024-05-04-computing-resources-cpu/intel-80486dx2-large.jpg
---

<br>

> 2024/05/04: 초안 작성
> 2024/05/05: CPU 성능 영향 요소 내용 보완
> 2024/05/08: CPU 구조 테이블 수정, Clock 내용, CPU Processing Cycle and Flow 추가

※ 내용에 오류가 있을 수 있습니다.  
※ 내용을 계속 추가, 수정, 보완하고 있습니다.

<br>

**목차**

- [CPU 구조](#cpu-구조)
- [1. CPU 작동원리](#1-cpu-작동원리)
- [2. CPU 프로세싱 주기와 흐름 Fetch-Decode-Execute-(Writeback) Cycle](#2-cpu-프로세싱-주기와-흐름-fetch-decode-execute-writeback-cycle)
- [3. CPU 성능에 영향을 미치는 요소들](#3-cpu-성능에-영향을-미치는-요소들)
  - [클럭 신호 Clock Signal는 어떻게 만들어지나](#클럭-신호-clock-signal는-어떻게-만들어지나)
- [관련 용어](#관련-용어)
- [4. 앞으로 알아야 할 CPU 기본 개념](#4-앞으로-알아야-할-cpu-기본-개념)
- [참고자료](#참고자료)

<br>


## CPU 구조

<br>

| 구성요소 | 요약 | 설명 |
| ----------- | --------------------------- | --------------------------- | 
| ALU (Arithmetic Logic Unit, 산술 논리 유닛) | 데이터에 대한 산술 및 논리 연산 수행 | 덧셈, 뺄셈, AND, OR, 비교 등의 연산 |
| 레지스터 | CPU 내에 위치한 데이터 임시 저장하는 소형 고속 메모리 장치 | Program Counter (PC), Instruction Register (IR), Accumulator, General Purpose Registers (GPRs) |
| Control Unit (CU) | CPU의 작동을 조정하고 메모리에서 명령을 가져와 디코딩 및 실행 | 메모리에서 명령어를 가져와 디코딩하고, 신호를 전송하여 ALU 및 레지스터를 제어 |
| Memory Management Unit (MMU, 메모리 관리 유닛) | 논리 메모리 주소를 물리적 주소로 변환하여 메모리 액세스를 관리 | 논리 메모리 주소를 물리적 주소로 변환하고 메모리 보호 및 액세스 제어를 수행 |
| 캐시 메모리 | CPU와 가까운 곳에 위치한 고속 메모리로 자주 액세스하는 데이터와 명령어를 저장 | L1 cache, L2 cache, L3 cache로 구성되고 CPU 아키텍처마다 다르지만 인텔의 경우 L1, L2는 코어마다 구성하고 L3는 CPU 외부에 위치시키거나 코어들이 공유함 |
| Instruction Decoder 명령 디코더| 디코더 메모리에서 가져온 명령어를 디코딩하고 실행하기 위한 제어 신호 | 명령어를 디코딩하여 수행할 작업을 결정 |
  
<br>

## 1. CPU 작동원리

<br>

- Fetch-Decode-Execute Cycle: CPU는 메모리에서 명령어를 가져와서 디코딩하고 실행하는 반복적인 주기로 명령어를 실행

- ISA (Instruction Set Architecture): CPU가 실행할 수 있는 명령 세트와 해당 명령의 형식을 정의

- 클럭 속도: CPU가 명령을 실행하는 속도(헤르츠(Hz))로 측정됨. 클럭 속도가 높을수록 일반적으로 처리 속도가 빨라지나 전력 소비와 발열이 많아짐.

- 파이프라인: CPU는 여러 명령의 실행을 겹쳐서 성능을 향상시키기 위해 파이프라인을 사용할 수 있음.

- 병렬성: 최신 CPU에는 여러 개의 코어가 있어 병렬 처리를 통해 여러 명령을 동시에 실행할 수 있음.

<br>

## 2. CPU 프로세싱 주기와 흐름 Fetch-Decode-Execute-(Writeback) Cycle

<br>

- CPU는 Fetch-Decode-Execute-(Writeback) Cycle을 반복함.

- Fetch: Control Unit은 실행할 다음 명령어의 메모리 주소를 Program Counter (PC)에서 가져옴.

- Decode: Instruction Decoder가 가져온 명령을 디코딩하여  명령 옵코드 Instruction opcode (Operation Code)에 따라 수행할 동작을 결정함.

- Execute:  Control Unit는 명령어 실행을 조정하며, 여기에는 ALU를 사용한 산술 또는 논리 연산 수행, 메모리 액세스 또는 레지스터 간 데이터 전송이 포함될 수 있음.

- Writeback (선택 사항): 경우에 따라 실행 결과를 레지스터나 메모리 위치에 다시 기록해야 할 수도 있음. 현재 명령어가 실행되면 프로그램 카운터 Program Counter에 다음 명령어를 가리키도록 기록되고, 다음 명령어에 대해 이 사이클이 순서대로 반복됨.

<br>

## 3. CPU 성능에 영향을 미치는 요소들

<br>

- CPU 성능은 클럭 속도, 캐시 크기, 명령 실행 효율성, 병렬성, 메모리 대역폭, 전력 소비 및 열 방출이 영향을 미침.

<br>

| 영향 요인 | 설명 | 성능에 미치는 영향 |
|---------------|----------------------------------------------|-----------------------------------------------|
| **클럭 속도** | CPU가 명령을 실행하는 속도 | 클럭 속도가 높을수록 일반적으로 처리 속도가 빨라짐. |
| **캐시 크기** | 자주 액세스하는 데이터를 저장하는 데 사용할 수 있는 고속 메모리의 양 | 캐시 크기가 클수록 일반적으로 성능이 향상 |
| **명령 실행 효율성** | 처리지시 효율성 Efficiency of processing instructions | 보다 효율적인 실행으로 전반적인 성능 향상|
| **병렬성** | 여러 명령을 동시에 실행하는 CPU의 능력 | 병렬성은 성능을 획기적으로 향상 가능 |
| **메모리 대역폭** | CPU와 메모리 간에 데이터가 전송될 수 있는 속도 | 더 높은 메모리 대역폭으로 전체 시스템 성능 향상|
| **전력 소비 및 열 방출** | 실행되는 동안 소비전력량 및 발열량 | 높은 전력 소비와 열로 인해 CPU 성능이 제한될 수 있음. |

<br>

### 클럭 신호 Clock Signal는 어떻게 만들어지나

<br>

- 클럭 신호는 System clock generator 또는 Simply the clock generator가 만듦.

- 일정한 속도로 전기 펄스 electrical pulses를 생성하고, 클럭 속도 clock speed 또는 클럭 주파수 clock frequency라고 함. 

- 클럭 신호는 CPU 내의 다양한 구성 요소의 작동을 서로 맞추고(동기화)하고 처리 사이클 속도를 말해주게 됨.

<br>

**클럭 속도 Clock Speed**

- 클럭 속도 Clock Speed는 헤르츠(Hz) 단위로 측정되는 클럭 속도는 CPU가 명령을 실행하는 속도를 나타냄.

- 클럭 속도가 높을수록 CPU가 초당 더 많은 명령을 수행할 수 있다는 의미

- 일반적으로 클럭 속도가 높을수록 처리 속도가 빨라지나 클럭 속도를 높이면 전력 소비와 발열도 높아짐.

<br>

## 관련 용어

<br>

**캐시 크기 Cache Size**

- 캐시 크기 Cache Size (CPU 캐시)란 CPU 다이(Die) 위나 근처에 위치한 소형 고속 메모리의 크기

- 자주 액세스하는 데이터와 명령을 저장하여 메모리 액세스 대기 시간을 줄임.
  
- 캐시 크기가 클수록 일반적으로 캐시에서 요청된 데이터나 명령을 찾을 가능성이 높아지고 느린 주 메모리에서 해당 데이터를 가져올 필요성이 줄어들기 때문에 성능이 향상됨.

<br>

**명령어 실행 효율성 Instruction Execution Efficiency**

<br>

- 명령어 실행 효율성 Instruction Execution Efficiency이란 CPU가 명령어를 얼마나 효율적으로 처리하는지를 나타냄.

- 효율성에 영향을 미치는 요소에는 CPU의 마이크로아키텍처 설계, ISA(Instruction Set Architecture) 및 파이프라이닝 기능이 포함됨.

- 보다 효율적인 명령 실행 기능을 갖춘 CPU는 클록 주기당 더 많은 작업을 수행할 수 있어 전반적인 성능이 향상됨.

- 더 넓은 명령 파이프라인이나 향상된 분기 예측과 같은 마이크로 아키텍처의 개선은 효율성을 크게 향상시킬 수 있음.

<br>

**병렬성 Parallelism**

<br>

- 병렬성이란 파이프라이닝, 수퍼스칼라 실행 Superscalar execution, 다중 코어 Multiple cores와 같은 기술을 통해 여러 명령을 동시에 실행할 수 있는 CPU의 능력을 말함.

- 병렬성은 CPU가 여러 명령을 동시에 실행할 수 있도록 하여 성능을 크게 향상시킬 수 있음.

- 멀티 코어 CPU는 명령을 병렬로 실행할 수 있는 여러 처리 장치를 제공하여 병렬성을 더욱 향상시킴.

<br>  

**메모리 대역폭 Memory Bandwidth**

<br>

- 메모리 대역폭이란 CPU와 메인 메모리 간에 데이터가 전송될 수 있는 속도를 나타냄.

- 메모리 대역폭은 메모리 속도, 메모리 버스 폭, 메모리 컨트롤러 효율성과 같은 요인에 따라 달라짐.

- 메모리 대역폭이 높을수록 CPU가 메모리에서 데이터에 더 빠르게 액세스할 수 있어 메모리 액세스 대기 시간이 줄어들고 특히 메모리 집약적인 작업에서 전반적인 시스템 성능이 향상됨.

<br>

**전력 소비 및 열 방출 Power Consumption and Heat Dissipation**

<br>

- 과도한 열은 과열을 방지하기 위해 CPU가 클럭 속도를 줄이는 열 조절로 이어질 수 있음.

- 최적의 성능을 유지하려면 효율적인 전력 관리 및 냉각 솔루션이 필수적

<br>

## 4. 앞으로 알아야 할 CPU 기본 개념

- 캐싱: 캐시 수준(L1, L2, L3), 캐시 연관성, 캐시 일관성을 포함한 캐싱의 기본 사항을 알아야 함.

- 명령어 세트: x86, ARM, MIPS 등의 일반적인 명령어 세트와 어셈블리 언어 프로그래밍을 알 필요가 있음.

- 전원 관리: 동적 주파수 조정 및 저전력 상태(예: 절전, 최대 절전 모드)와 같은 CPU 절전 기능에 유의해야 함.

- 성능 최적화: 알고리즘 최적화, 병렬 처리, 캐시 인식 프로그래밍 등 CPU 성능 최적화 기술에 대하여 알아야 함.


  
<br>
<br>

## 참고자료

[Wikipedia] Central processing unit
<https://en.wikipedia.org/wiki/Central_processing_unit>

[Wikipedia] Arithmetic logic unit
<https://en.wikipedia.org/wiki/Arithmetic_logic_unit>

[Wikipedia] Processor register  
<https://en.wikipedia.org/wiki/Processor_register>

[Wikipedia] Control unit  
<https://en.wikipedia.org/wiki/Control_unit>


