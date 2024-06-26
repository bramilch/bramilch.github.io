---
layout: post
title: "컴퓨팅 4대 리소스 - 디지털 회로 측면에서의 메모리 Memory 유형별 차이"
author: bramilch
date: 2024-05-18 18:00:00 +0900
categories: [Backend, Data Engineering]
tags: [Backend, Data Engineering]
pin: true
math: false
toc: true
comments: false
mermaid:
  false
  # alt: Responsive rendering of Chirpy theme on multiple devices.
image:
  path: ./assets/img/posts/2024-05-01-memory-types-differences/dram_Inside.png
---

<br>

> 2024/05/18: 초안 작성  
> 2024/05/19: 문장 수정
 
※ 내용에 오류가 있을 수 있습니다.  
※ 내용을 계속 추가, 수정, 보완하고 있습니다.  

<br>

**목차**

- [RAM에 사용되는 재료 및 장치](#ram에-사용되는-재료-및-장치)
- [디지털 회로 측면에서의 SRAM, DRAM, NAND 플래시 메모리, SDRAM, DDR SDRAM 구성](#디지털-회로-측면에서의-sram-dram-nand-플래시-메모리-sdram-ddr-sdram-구성)
- [메모리별 디지털 회로 구조의 차이점](#메모리별-디지털-회로-구조의-차이점)
- [메모리별 특징에 따른 용도 차이](#메모리별-특징에-따른-용도-차이)

<br>

- 5월 1일에 포스팅한 '컴퓨팅 4대 리소스 - 메모리 Memory 유형별 차이'에선 전반적이고 포괄적으로 SRAM, DRAM, NAND 플래시 메모리, SDRAM, DDR SDRAM의 용도 차이, 플립플롭, 커패시터, NAND Gate와 메모리, 캐시, 버퍼 등에 대해 살펴보았음.

- 디지털 회로는 SRAM, DRAM, NAND 플래시 메모리, SDRAM 및 DDR SDRAM과 같은 메모리 기술을 포함한 전자 장치의 기초

- SRAM, DRAM, NAND 플래시 메모리, SDRAM, DDR SDRAM 간의 속도와 특성 차이는 기본 하드웨어 및 디지털 회로 설계에서 비롯됨.

- 실리콘 기반 트랜지스터, 커패시터, 다이오드 등 디지털 회로에 사용되는 재료와 장치는 SRAM, DRAM, NAND 플래시 메모리, SDRAM, DDR SDRAM과 같은 메모리 기술의 작동에서 각기 다른 역할을 함.

- SRAM은 비스테이블 래치 Bistable Latch 설계로 인해 가장 빠르므로 캐시 메모리에 적합

- DRAM은 속도가 느리고 주기적으로 새로 고쳐야 하므로 메인 메모리에 적합

- NAND 플래시는 비휘발성이며 내구성이 높지만 속도가 느리고 쓰기 횟수가 제한되어 있어 기본 메모리보다는 스토리지에 적합

- SDRAM과 DDR SDRAM은 동기식 및 휘발성이며, DDR은 SDRAM의 두 배에 달하는 데이터 속도를 제공하므로 고속 메모리 애플리케이션에 적합

<br>

<center><span style="font-size:1.2em;">SRAM, DRAM, NAND Flash, SDRAM, DDR SDRAM 메모리 비교</span></center>

<br>

| 메모리 종류 | 재료 및 장치 | 구조 및 원리 | 역할 | 휘발성 및 속도 |
| ------------------------ | ------------------------------------- | ------------------------------------- | ------------------------------------- | ------------------------------------- |
| SRAM | 실리콘 기반 트랜지스터, 바이스테이블 래치 설계(Bistable Latch,  Flip-flop Design), 크로스 커플링 트랜지스터(Cross-Coupled Transistors) | 주요 구조 원리는 바이스테이블 래치(Bistable Latch)와 크로스 커플링 트랜지스터(Cross-Coupled Transistors)임. 비스테이블 래치(Bistable Latch)는 데이터를 이진 형식(0 또는 1)으로 저장하는 플립플롭으로 구성됨. 크로스 커플링 트랜지스터(Cross-Coupled Transistors)는 플립플롭 설계에 사용되어 저장된 데이터에 빠르게 액세스하고 수정할 수 있게 해줌. | 임시 저장(캐시)을 위한 가장 빠른 메모리, 휘발성(데이터 유지를 위해 전원이 필요함) | 휘발성(데이터 유지를 위해 지속적인 전원 공급이 필요), 속도는 바이스테이블 래칭 회로(Bistable latching circuitry)로 인해 앞서 언급한 유형 중 가장 빠름 |
| DRAM | 실리콘 기반 트랜지스터, 데이터 스토리지용 커패시터, 트랜지스터-트랜지스터 로직(TTL, Transistor-Transistor Logic)| 주요 구조 원리는 커패시터와 TTL, Refresh 주기임. 커패시터는 데이터를 전하로 저장, 트랜지스터-트랜지스터 로직(TTL)는 트랜지스터를 사용하여 신호를 증폭, 약 64밀리초마다 Refresh로 전원 공급 필요 | 일반 컴퓨팅 작업을 위한 주 메모리, 휘발성(전원이 없으면 데이터 손실) | 휘발성(전원이 꺼지면 데이터가 손실), Refresh 주기가 필요(데이터 무결성을 유지하기 위해 주기적으로 Refresh 필요) |
| NAND 플래시 | 플래시 실리콘 기반 트랜지스터, 플로팅 게이트 MOSFET(Floating-Gate MOSFETs), 플로팅 게이트용 ONO 3중층(ONO trilayer) | 주요 구조 원리는 플래시 플로팅 게이트와 Program/Erase Mechanism, Page Structure임. 플래시 플로팅 게이트 MOSFET(Floating-Gate MOSFETs)는 제어 게이트로 둘러싸인 플로팅 게이트를 활용, 프로그램/지우기 메커니즘(Program/Erase Mechanism)은 플로팅 게이트에 전자를 주입하여 데이터를 쓰고, 전자를 제거하여 데이터를 지움. Page Structure는 NAND 플래시에서 데이터는 페이지로 구성됨을 의미 | 플래시 비휘발성 스토리지(예: USB 드라이브, SSD), 쓰기 횟수 제한적 | 비휘발성(전원 없이도 데이터를 유지), 쓰기 주기 제한(성능 저하가 발생하기 전 쓰기 횟수가 한정되어 있음) |
| SDRAM | 실리콘 기반 트랜지스터, 데이터 저장용 커패시터, 시스템 클록과 동기(Synchronous) 작동 | 주요 구조 및 작동 원리는 DRAM Cells, Synchronous Operation, CAS Latency임. DRAM 셀(DRAM Cells)는 커패시터와 트랜지스터로 구성된 저장 장치의 기본 단위. 동기식 작동(Synchronous Operation)은 클럭 신호의 상승 Edge에서 데이터 전송이 발생하는 구조. CAS 지연 시간(CAS Latency)는 메모리 컨트롤러가 데이터를 요청하는 순간과 요청된 데이터를 사용할 수 있는 순간 사이의 지연을 측정함 | 일반 컴퓨팅 작업용 메인 메모리, 시스템 클럭과 동기 작동 | 휘발성(전원이 꺼지면 데이터가 손실됨), 동기식(Synchronous, 시스템 클록과 동기화하여 작동함) |
| DDR SDRAM | 실리콘 기반 트랜지스터, 데이터 스토리지용 커패시터, 이중 데이터 전송률(Double data rate, 클록 신호의 양쪽 Edge에서 데이터 전송(transfers data on both edges of the clock signal)) | 주요 구조 및 작동 원리는 DDR Architecture, Banked Architecture, CAS Latency and RAS to CAS Delay (tRCD)임. DDR 아키텍처는 클럭 신호의 상승 Edge와 하강 Edge 모두에서 데이터를 전송하여 데이터 속도를 향상시킴. 뱅크 아키텍처(Banked Architecture)는 메모리를 뱅크 Bank로 분할하여 동시 액세스가 가능하게 함. CAS 지연 시간 및 RAS에서 CAS로의 지연(tRCD, CAS Latency and RAS to CAS Delay)는 성능에 영향을 미치는 주요 매개변수임 | 일반 컴퓨팅 작업을 위한 메인 메모리, 이중 데이터 전송률로 인한 더 높은 데이터 전송률 | 휘발성(전원이 꺼지면 데이터가 손실됨), 더블 데이터 전송률(Double data rate)는 클록 사이클당 데이터를 두 번 전송함 |

<br>

## RAM에 사용되는 재료 및 장치

<br>

**실리콘 기반 디바이스**

<br>

- 실리콘(Si, Silicon): 트랜지스터와 다이오드를 포함한 반도체 소자에 사용되는 주요 재료. 특정 조건에서 전기를 전도하는 실리콘은 디지털 회로에 필요한 초소형 스위치와 증폭기를 만드는 데 이상적

- 게르마늄(Ge, Germanium): 초기 트랜지스터에 사용되었으나 전자 이동도(Electron mobility)가 높고 제조 비용이 낮은 실리콘으로 대체되었음.

<br>

**트랜지스터**

<br>

- ***디지털 회로에서 스위치 또는 증폭기 역할을 함.***

-  ***SRAM과 DRAM에서는 커패시터에 저장된 데이터를 읽고 쓰는 데 사용됨. NAND 플래시 메모리에서는 플로팅 게이트로 들어오고 나가는 전류의 흐름을 제어***

<br>

**다이오드 Diodes**

<br>

- 전류 흐름의 방향을 제어하여 특정 회로에서 원치 않는 전류 경로를 방지하기 위한 장벽 역할을 함.

<br>

**커패시터 Capacitors**

<br>

- 유전체 재료(Dielectric Materials): 전기 에너지를 저장하기 위해 커패시터의 플레이트 Plate 사이에 배치되는 절연 재료. 일반적인 유전체에는 이산화규소 Silicon Dioxide(DRAM에 사용), 오산화탄탈륨(Tantalum Pentoxide), 산화알루미늄(Aluminum Oxide) 등이 있음.

- 금속판 Metal Plates: 유전체 재료로 분리된 전도성 판으로 커패시터의 기본 구조를 형성

- ***DRAM에 데이터를 나타내는 전하를 저장, SRAM에선 임시 저장 요소 역할을 함. NAND 플래시 메모리에서 커패시터는 플로팅 게이트 구조의 일부***

<br>

**플로팅 게이트 트랜지스터 Floating-Gate Transistors (NAND 플래시 메모리에 사용)**

<br>

- 산화물-질화물-산화물(ONO) 3중층(Oxide-Nitride-Oxide (ONO) Trilayer): 이산화규소, 질화규소, 또 다른 이산화규소 층으로 구성. 3중층은 낸드 플래시 셀에서 플로팅 게이트를 형성하여 데이터를 나타내는 전하를 저장할 수 있도록 함.


<br>

## 디지털 회로 측면에서의 SRAM, DRAM, NAND 플래시 메모리, SDRAM, DDR SDRAM 구성

<br>

**SRAM(정적 랜덤 액세스 메모리)**

<br>

- 재료: 주로 실리콘 기반 트랜지스터로, 로직 게이트 Logic gates와 메모리 셀 Memory cells을 만들기 위한 기본 구성 요소 역할

- 장치: 일반적으로 ***크로스 결합 트랜지스터(플립플롭)***로 구현되는 바이스테이블 래치 회로를 활용. 이러한 플립플롭은 지속적인 전원 공급 없이도 데이터를 이진 형식(0 또는 1)으로 저장

<br>

**DRAM(동적 랜덤 액세스 메모리)**

<br>

- 재료: SRAM과 마찬가지로 DRAM은 실리콘 기반 트랜지스터를 사용. 데이터를 임시로 저장하기 위해 커패시터를 사용

- 장치: ***DRAM 셀의 핵심은 커패시터와 트랜지스터로 구성. 커패시터는 데이터 비트(0 또는 1)를 나타내는 전하를 보유하고, 트랜지스터는 커패시터에서 데이터를 읽거나 쓰기 위한 스위치 역할을 함.*** SRAM과 달리 DRAM 셀은 전원이 제거되면 콘텐츠가 손실되므로 주기적으로 Refresh 필요

<br>

**낸드 플래시 메모리**

<br>

- 재료: 실리콘 기반 트랜지스터와 커패시터용 특수 유전체 재료가 포함됨. ***독특한 특징은 플로팅 게이트 MOSFET(Metal-Oxide-Semiconductor Field-Effect Transistor)을 사용한다는 점***

- 장치: 플로팅 게이트 MOSFET은 데이터를 갇힌 전하로 저장. 이 구조는 비휘발성이므로 전원이 차단되어도 데이터가 그대로 유지. 낸드 플래시 메모리는 페이지 Pages로 구성되어 있어 효율적인 삭제 및 프로그래밍이 용이

<br>

**SDRAM(Single Data Rate Synchronous Dynamic RAM)**

<br>

- 재료: DRAM과 유사한 실리콘 기반 트랜지스터와 커패시터를 사용

- 장치: SDRAM은 시스템 클럭에 동기화하여 클럭 신호에 의해 정의된 일정한 간격으로 데이터 전송이 이루어지도록 함. ***이러한 동기식 작동은 프로세서와 메모리 액세스를 조정하는 데 도움이 됨.***

<br>

**DDR SDRAM(Double Data Rate Synchronous Dynamic RAM)**

<br>

- 재료: SDRAM과 마찬가지로 DDR SDRAM은 실리콘 기반 트랜지스터와 커패시터를 사용

- 장치: ***DDR SDRAM의 특징은 클록 신호의 상승 및 하강 에지 모두에서 데이터를 전송할 수 있어(Double Data Rate) SDRAM에 비해 데이터 전송 속도가 효과적으로 두 배가 된다는 것.*** 이는 효율적인 데이터 처리를 가능하게 하는 보다 정교한 타이밍 프로토콜을 통해 달성할 수 있음.

<br>


## 메모리별 디지털 회로 구조의 차이점

<br>

**SRAM과 DRAM 비교**

<br>

- 셀 구조: ***SRAM은 셀당 6개의 트랜지스터(읽기용 2개, 쓰기용 2개, 상태 유지용 2개)를 사용하는 반면, DRAM은 셀당 1개의 트랜지스터와 1개의 커패시터를 사용***

- 읽기/쓰기 작업: ***SRAM은 트랜지스터를 통해 직접 데이터를 읽고 쓰므로 더 빠르지만 전력 소모가 더 큼. DRAM은 트랜지스터를 통해 데이터를 읽고 커패시터에 저장하므로 데이터 무결성을 유지하기 위해 주기적으로 전기를 공급하는 Refresh 필요***

<br>

**낸드 플래시 메모리**

<br>

- ***플로팅 게이트 모스펫 구조 Floating-Gate MOSFETs: 제어 게이트로 둘러싸인 플로팅 게이트가 특징인 낸드 플래시 고유의 구조. 플로팅 게이트에 저장된 전하가 데이터를 나타냄.***

- 프로그램/지우기 메커니즘 Program/Erase Mechanism: ***플로팅 게이트에 전자를 주입하여 데이터를 쓰고, 전자를 제거하여 데이터를 지움. 이 메커니즘은 높은 내구성을 제공하지만 쓰기 주기가 제한됨.***

**SDRAM과 DDR SDRAM 비교**

- ***클록 동기화 Clock Synchronization***: SDRAM과 DDR SDRAM은 모두 동기식이기 때문에 시스템 클럭과 동기화되어 작동. 그러나 DDR SDRAM은 클럭 신호의 상승 및 하강 에지 모두에서 데이터를 전송하여 데이터 전송 속도를 두 배로 높여 SDRAM을 개선

- ***뱅크형 아키텍처 Banked Architecture: 두 유형 모두 메모리를 별도의 뱅크로 나누어 메모리의 서로 다른 부분에 동시에 액세스할 수 있는 뱅크형 아키텍처를 사용. DDR SDRAM은 더 높은 성능을 위해 이 아키텍처를 더욱 최적화***

<br>

## 메모리별 특징에 따른 용도 차이

**SRAM과 DRAM 비교**

<br>

- 역할: SRAM은 컴퓨터에서 캐시 메모리 역할을 하며 자주 사용하는 데이터에 빠르게 액세스할 수 있도록 함. DRAM은 느리지만 가격이 저렴하여 주 메모리로 사용됨.

- 구조적 차이: SRAM은 바이스테이블 래치 설계를 사용하므로 더 빠르지만 전력 소모가 더 큼. DRAM은 데이터 저장에 커패시터를 사용하므로 데이터 무결성을 유지하기 위해 주기적으로 전기를 공급하는 Refresh를 해야 함.

<br>

**낸드 플래시 메모리**

<br>

- 역할: 주로 USB 드라이브, SSD, 임베디드 시스템과 같은 장치의 비휘발성 스토리지에 사용됨.

- 구조적 차이: 플로팅 게이트 구조는 비휘발성과 높은 내구성을 제공하지만 쓰기 횟수가 제한됨.

<br>

**SDRAM과 DDR SDRAM 비교**

<br>

- 역할: 둘 다 컴퓨터의 주 메모리 역할을 하며, DDR SDRAM은 이중 데이터 전송률 기능으로 인해 더 높은 데이터 전송률을 제공

- 구조적 차이: DDR SDRAM은 클럭 신호의 양쪽 에지에서 데이터를 전송하는 기능을 통해 더 높은 성능을 달성하여 전체 시스템 처리량을 향상시킴.


