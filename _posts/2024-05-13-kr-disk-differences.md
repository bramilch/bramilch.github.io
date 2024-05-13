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


