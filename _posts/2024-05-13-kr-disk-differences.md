---
layout: post
title: "컴퓨팅 4대 리소스 - 디스크 종류와 특성 비교"
author: bramilch
date: 2024-05-06 18:00:00 +0900
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
  path: ./assets/img/posts/2024-05-13-kr-disk-differences/640px-Seagate_ST33232A_hard_disk_inner_view.jpg
---

<br>

> 2024/05/13: 초안 작성
> 2024/05/14: 각 Disk 종류별 설명과 특징 추가

※ 내용에 오류가 있을 수 있습니다.  
※ 내용을 계속 추가, 수정, 보완하고 있습니다.

<br>

**목차**

- [HDD, SSD, HHD, Optical Disk, RAID 개념, 특징](#hdd-ssd-hhd-optical-disk-raid-개념-특징)
- [](#)
- [](#-1)
- [](#-2)
- [참고자료](#참고자료)

<br>


## HDD, SSD, HHD, Optical Disk, RAID 개념, 특징

<br>


- HDD는 GB당 저렴한 비용으로 대용량 스토리지를 제공하지만 액세스 시간이 느리고 기계적 고장에 더 취약

- SSD는 더 빠른 성능, 낮은 전력 소비, 향상된 내구성을 제공하지만 일반적으로 GB당 가격이 더 비쌈.

- 하이브리드 HHD (Hybrid Hard Disk Drive)는 HDD의 저장 용량과 SSD 캐싱의 성능 이점을 결합하여 비용, 용량, 성능 간의 균형을 제공

- 광 디스크 Optical Disk는 아카이브 목적으로 대량의 데이터를 저장하거나 소프트웨어 및 멀티미디어 콘텐츠를 배포하는 데 적합

- RAID는 여러 개의 물리적 디스크를 단일 논리 장치로 결합하여 데이터 중복성 및/또는 성능 최적화를 제공하며, 사용 사례에 따라 다양한 구성을 사용할 수 있음.


<br>

- 하드 디스크 드라이브(HDD, Hard Disk Drive)
  
  - 하드 디스크 드라이브(HDD)는 자성 물질로 코팅된 회전식 플래터 rotating platters를 사용하여 데이터를 저장하는 전통적인 기계식 저장 장치. 데이터는 플래터를 가로질러 움직이는 마그네틱 헤드를 사용하여 읽고 씀.

  - 특징  
    - GB당 비용이 상대적으로 저렴
    - SSD에 비해 액세스 시간이 느림
    - 더 높은 용량의 스토리지 사용 가능
    - 움직이는 부품으로 인한 기계적 고장 및 데이터 손실에 취약
    - 대량 저장 및 보관 목적에 적합

<br>

- SSD(Solid State Drive, 솔리드 스테이트 드라이브):

  - SSD는 플래시 메모리 칩을 사용하여 데이터를 전자적으로 저장하는 저장 장치. 움직이는 부품이 없기 때문에 HDD에 비해 액세스 시간이 빠르고 내구성이 좋음.

  - 특징
    -HDD에 비해 GB당 비용이 더 높음.
    -읽기 및 쓰기 속도가 빨라 시스템 부팅 시간 및 애플리케이션 로딩 시간이 단축됨.
    -전력 소비와 발열이 적음.
    -기계적 고장이 HDD보다 덜 취약
    -데이터베이스, 가상화, 게임 등 고성능 컴퓨팅 작업에 적합함.

<br>

- 하이브리드 HHD (Hybrid Hard Disk Drives):


  - 하이브리드 HHD는 기존의 회전식 HHD 플래터와 캐시 역할을 하는 소량의 솔리드 스테이트 메모리(보통 NAND 플래시)를 결합한 것

  - 특징
    - HDD의 대용량 저장 용량과 SSD의 빠른 액세스 시간 사이의 균형을 제공합
    - SSD 캐시로 인해 자주 액세스하는 데이터의 성능이 향상
    - 순수 SSD에 비해 비용이 저렴
    - SSD 캐시 크기가 제한되어 있어 순수한 SSD보다 대용량 데이터 세트에 대한 성능 이점이 감소할 수 있음.

<br>

- 광학 디스크 Optical Disk:


  - CD, DVD, 블루레이 디스크와 같은 광학 디스크는 레이저 광선을 사용하여 반사 표면에 저장된 데이터를 읽고 씀.

  - 특징
    - GB당 비용이 상대적으로 저렴
    - 읽기 전용(CD-ROM, DVD-ROM) 또는 쓰기 가능(CD-R, DVD-R) 포맷을 사용할 수 있음.
    - HDD 및 SSD에 비해 데이터 전송 속도가 느림.
    - 아카이브 목적으로 대량의 데이터를 저장하거나 소프트웨어 및 멀티미디어 콘텐츠를 배포하는 데 적합

<br>

- RAID(Redundant Array of Independent Disks):


  - RAID는 데이터 중복성, 성능 향상의 두 가지 목적을 위해 여러 개의 물리적 디스크 드라이브를 하나의 논리 단위로 결합하는 데이터 스토리지 기술

  - 특징
    - 다양한 RAID 레벨은 중복성(RAID 1, RAID 5, RAID 6) 및 성능(RAID 0, RAID 10)을 위한 다양한 구성을 제공
    - 여러 디스크에 데이터를 복제(미러링)하거나 오류 수정을 위해 패리티 데이터 Parity data를 사용해 내결함성을 제공
    - 여러 디스크에 데이터를 분산하여 읽기 및/또는 쓰기 성능을 향상시킴.
    - 데이터 보호 및 성능 최적화를 위해 서버, NAS(네트워크 연결 스토리지) 장치 및 엔터프라이즈 스토리지 시스템에서 사용됨.


<br>

<center><span style="font-size:1.2em;"> 디스크 종류별 비교 </span></center>

<br>

| 종류 | 설명 | 장점 | 단점 | 용도 |
|  ------------------- | ------------------- | ------------------- | ------------------- | ------------------- |
| HDD(하드 디스크 드라이브)|  자성 물질로 코팅된 회전 디스크를 데이터 저장에 사용 | 	대용량 저장 용량(단일 드라이브에서 최대 4TB), 읽기 및 쓰기 작업이 안정적이고 신뢰할 수 있음 	| 속도가 느리고 전력 소비가 높으며 소음이 발생,  진동으로 인한 충돌 및 손상에 취약 | 데이터 저장소, 백업 시스템, 메일 서버, 비디오 스트림, VM용 서버 등 데이터를 자주 읽거나 쓰지 않는 작업에 적합 |
| SSD(솔리드 스테이트 드라이브)|  데이터 저장에 플래시 메모리 칩을 사용, HDD처럼 물리적으로 움직이는 부품이 없음 | 읽기/쓰기 속도가 빠르고, 전력 소비가 적으며, 소음이 적고, 진동에 대한 내구성이 뛰어남 | 	일반적으로 HDD에 비해 기가바이트당 가격이 더 비쌈 	| 고속 작업, 최신 CMS (Content Management System)로 개발된 웹사이트, 빠른 데이터 액세스가 필요한 애플리케이션 등 읽기 및 쓰기 작업이 많은 고부하 프로젝트에 적합 |
| 광 디스크 Optical Disk | CD, DVD, 블루레이 디스크 | 데이터는 반사되는 표면에 저장 	| 블루레이 디스크의 경우 단일 레이어에 최대 25GB까지 저장할 수 있는 광학 미디어의 대용량 저장 장치 | HDD, SSD에 비해 데이터 액세스 속도가 느림. 물리적 미디어가 손상되거나 분실될 수 있음 	| 비디오 파일, 음악, 소프트웨어 설치 등 대용량의 데이터를 저장하고 배포하는 데 사용 |
| RAID (Redundant Array of Independent Disks) | 드라이브 장애 시 데이터를 보호하기 위해 동일한 데이터를 여러 하드디스크의 서로 다른 위치에 저장하는 방식 | 	데이터 중복성 및 성능 향상을 제공 | 설정 및 관리가 복잡, 제대로 구성하지 않으면 데이터 손실 위험 	| 데이터베이스 서버, 웹 서버, 금융 시스템 등 데이터 무결성과 성능이 중요한 서버 및 스토리지 시스템에 사용 |

  
<br>

## 

<br>



<br>

## 


<br>

## 

<br>



  
<br>
<br>

## 참고자료

[Wikipedia] Hard disk drive
<https://en.wikipedia.org/wiki/Hard_disk_drive>

[Wikipedia] Solid-state drive
<https://en.wikipedia.org/wiki/Solid-state_drive>

[Wikipedia] Hybrid drive
<https://en.wikipedia.org/wiki/Hybrid_drive>


