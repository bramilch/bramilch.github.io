---
layout: post
title: 데이터베이스 설계 - Non Relational DB 편
author: bramilch
date: 2024-07-07 18:00:00 +0900
categories: [Backend, Data Engineering]
tags: [Backend, Data Engineering]
pin: true
math: false
toc: true
comments: false
mermaid: false
---

<br>

> 2024/07/07: 초안 작성  
 
※ 내용에 오류가 있을 수 있습니다.  
※ 내용을 계속 추가, 수정, 보완하고 있습니다.  

<br>

**목차**
- [머리말](#머리말)
- [비관계형 Non-Relational DB](#비관계형-non-relational-db)
- [비관계형 DB 동작 원리](#비관계형-db-동작-원리)


<br>

## 머리말

<br>

- '데이터베이스 설계 - RDB 편'에서 관계형 Relational DB 설계의 상향식, 하향식 설계, 하향식 설계 절차, 주요 고려 요소와 주의할 점들에 대해서 살펴봄.

- 여기선 정형, 반정형, 비정형 데이터 유형과 상황에 따른 비관계형 DB Non-Relational DB 특징, 설계 절차, 설계 시 고려 요소, 주의할 점, 설계 예시 등을 살펴보고자 함.

<br>

## 비관계형 Non-Relational DB

<br>

- 비관계형 데이터베이스(NoSQL DB)는 관계형 데이터베이스에서 사용되는 기존 표 형식의 관계에 기반하지 않는 다양한 데이터 모델을 처리하도록 설계되었음. 

- 특히 대량의 비정형, 반정형 또는 정형 데이터를 관리하는 데 적합. 

<br>

**NoSQL 데이터베이스의 주요 유형**

<br>

- 문서형 Document: MongoDB, CouchDB

- 키-값형 Key-Value: Redis, DynamoDB

- 컬럼 패밀리형 Column-Family: Cassandra, HBase

- 그래프형 Graph: Neo4j, ArangoDB

<br>

**왜 비관계형 데이터베이스를 사용하나?**

<br>

- 보통 기본적인 RDB를 사용하고, RDB의 한계를 넘어선 데이터 유형, 데이터 양 등 대량의 정형, 반정형, 비정형 데이터 특성과 환경에 따라 Non-relational DB를 선택

- 유연성 Flexibility: NoSQL 데이터베이스는 스키마가 없는 데이터 모델을 제공하므로 보다 유연하고 동적인 데이터 구조가 가능

- 확장성 Scalability: 수평적으로 확장할 수 있도록 설계되어 분산된 시스템에서 대규모 데이터를 보다 쉽게 처리할 수 있음.

- 성능 Performance: 높은 읽기/쓰기 처리량에 최적화된 NoSQL 데이터베이스는 특정 워크로드에 더 빠른 성능을 제공할 수 있음.

- 복잡한 데이터 Complex Data: 중첩된 문서나 그래프 데이터와 같은 복잡한 데이터 구조를 광범위한 조인 없이 처리하는 데 적합

<br>

## 비관계형 DB 동작 원리

<br>

- 대량의 비정형, 반정형 또는 정형 데이터를 처리하도록 설계되었으며 스키마 설계, 확장성 및 성능 측면에서 유연성을 제공합니다. 다음은 비관계형 데이터베이스의 작동 방식, 원리, 아키텍처 및 주요 차이점에 대한 개요

<br>

**원칙**

<br>

**스키마 유연성 Schema Flexibility**

- 고정된 스키마가 필요하지 않으므로 보다 동적인 데이터 모델을 사용할 수 있음. 시간이 지남에 따라 데이터 구조가 변할 수 있는 애플리케이션에 유용

**수평적 확장성 Horizontal Scalability**

- 여러 서버에 샤딩을 통해 데이터를 분산하여 확장할 수 있도록 설계함. 샤딩은 데이터를 더 작은 청크로 분할하여 여러 머신 클러스터에 저장할 수 있음.

**분산 아키텍처 Distributed Architecture**

- 분산 아키텍처에서 사용하여 데이터가 여러 노드에 복제되고 분할되도록 함. 이는 가용성, 내결함성, 확장성이 좋아짐.

**CAP 정리 CAP Theorem**

- 분산 시스템에서는 세 가지 중 두 가지만 달성할 수 있음. 1. 일관성, 가용성, 파티션 허용 오차. 2. 가용성과 파티션 허용, **이벤트성 일관성**을 우선시함.

> 이벤트성 일관성이란 Eventual consistency란 분산 NoSQL 데이터베이스에서 업데이트가 모든 노드에 반영되도록 보장하는 데이터 모델링 개념

**고성능 High Performance**

- 읽기/쓰기 성능에 최적화. 인메모리 스토리지와 데이터 검색 메커니즘 활용


<br>


<br>



<br>
<br>

[참고자료]

[DATA ON-AIR]성공적인 NoSQL 도입을 위한 키포인트 : NoSQL 데이터 모델링    
<https://dataonair.or.kr/db-tech-reference/d-lounge/technical-data/?mod=document&uid=236123>

[MongoDB] NOSQL 데이터 모델링 기법 살펴보기  
<https://velog.io/@hwaya2828/MongoDB-NOSQL-%EB%8D%B0%EC%9D%B4%ED%84%B0-%EB%AA%A8%EB%8D%B8%EB%A7%81-%EA%B8%B0%EB%B2%95-%EC%82%B4%ED%8E%B4%EB%B3%B4%EA%B8%B0>
