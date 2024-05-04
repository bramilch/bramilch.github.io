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
  path: ./assets/img/posts/2024-05-01-memory-types-differences/memory-types.png
---

<br>

> 2024/05/04: 초안 작성
 
※ 내용에 오류가 있을 수 있습니다.  
※ 내용을 계속 추가, 수정, 보완하고 있습니다.

<br>

**목차**

- [CPU 구조](#cpu-구조)
- [CPU 작동원리](#cpu-작동원리)
- [앞으로 알아야 할 CPU 기본 개념](#앞으로-알아야-할-cpu-기본-개념)
- [참고자료](#참고자료)

<br>


## CPU 구조

<br>

| 구성요소 | 설명 |
| ----------- | ---------------------------|
| ALU(산술 논리 장치) | 산술 및 논리 수행 | 덧셈, 뺄셈, AND, OR 등의 연산 |
| 레지스터 | 데이터를 저장하는 데 사용되는 소형 고속 메모리 장치 | 처리 중 일시적으로 |
| 제어 장치 Control Unit | 명령 실행 조정, 데이터 제어 | 흐름을 제어하고 CPU의 작동을 관리합니다 |
| 캐시 메모리 | CPU 또는 CPU 가까이에 위치한 고속 메모리 | 자주 액세스하는 데이터를 저장하는 데 사용 |
| 명령해독기 Instruction Decoder | 디코더 메모리에서 가져온 명령어를 디코딩하고 | 실행하기 위한 제어 신호 |
  
<br>

## CPU 작동원리

<br>

- Fetch-Decode-Execute Cycle: CPU는 메모리에서 명령어를 가져와서 디코딩하고 실행하는 반복적인 주기로 명령어를 실행

- ISA (Instruction Set Architecture): CPU가 실행할 수 있는 명령 세트와 해당 명령의 형식을 정의

- 클럭 속도: CPU가 명령을 실행하는 속도(헤르츠(Hz))로 측정됩니다. 클럭 속도가 높을수록 일반적으로 처리 속도가 빨라짐.

- 파이프라인: CPU는 여러 명령의 실행을 겹쳐서 성능을 향상시키기 위해 파이프라인을 사용할 수 있음.

- 병렬성: 최신 CPU에는 여러 개의 코어가 있어 병렬 처리를 통해 여러 명령을 동시에 실행할 수 있음.

<br>

## 앞으로 알아야 할 CPU 기본 개념

<br>

- CPU 성능: 클럭 속도, 캐시 크기, 명령 실행 효율성 등 CPU 성능에 영향을 미치는 요소를 이해해야함.

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


