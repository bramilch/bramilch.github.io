---
layout: post
title: 파이썬 가상환경 원리와 비교
author: bramilch
date: 2024-08-11 18:00:00 +0900
categories: [Backend, Data Engineering]
tags: [Backend, Data Engineering]
pin: true
math: false
toc: true
comments: false
mermaid: false
image:
  path: ./assets/img/posts/2024-07-07-kr-db-design-non-relational-DB/1024px-Advantages_of_NoSQL.png
---

<br>

> 2024/08/12: 초안 작성  

※ 내용에 오류가 있을 수 있습니다.  
※ 내용을 계속 추가, 수정, 보완하고 있습니다.  

<br>

**목차**
- [머리말](#머리말)
- [비관계형 Non-Relational DB](#비관계형-non-relational-db)
- [비관계형 DB 동작 원칙과 아키텍처, Non-RDB 간 차이](#비관계형-db-동작-원칙과-아키텍처-non-rdb-간-차이)
  - [원칙의 차이](#원칙의-차이)
  - [NoSQL DB 아키텍처](#nosql-db-아키텍처)
  - [NoSQL DB들 간의 차이점](#nosql-db들-간의-차이점)
- [NoSQL DB 설계 절차](#nosql-db-설계-절차)
  - [NoSQL DB 설계 시 고려 요소](#nosql-db-설계-시-고려-요소)
  - [NoSQL DB 설계 시 주의 사항](#nosql-db-설계-시-주의-사항)
- [RDB, NoSQL DB 통합하기](#rdb-nosql-db-통합하기)
- [Polyglot Persistence 다양한 언어, 도구 지속성](#polyglot-persistence-다양한-언어-도구-지속성)


<br>

## 요약

<br>

파이썬 가상 환경은 다양한 도구와 방법을 사용하여 만들 수 있으며, 각각 고유한 기능, 이점 및 사용 사례가 있습니다. 여기서는 가장 많이 사용되는 방법인 venv, virtualenv, virtualenvwrapper, pyenv 및 conda를 비교

각 도구는 고유한 강점을 가지고 있으며 다양한 사용 사례에 적합합니다:

venv: Python 3.3 이상의 간단한 기본 제공 환경 관리에 가장 적합합니다.
가상 환경: venv보다 더 많은 유연성과 옵션을 제공하며, 이전 Python 버전을 지원합니다.
가상 환경 래퍼: 보다 사용자 친화적인 인터페이스로 여러 가상 환경의 관리를 간소화합니다.
pyenv: 특히 개발 환경에서 여러 Python 버전을 관리하고 격리된 환경을 만드는 데 이상적입니다.
conda: 환경 및 종속성 관리를 위한 종합적인 도구로, 패키지 관리 기능이 있어 특히 데이터 과학 및 머신 러닝 프로젝트에 적합합니다.
적합한 도구를 선택하는 것은 특정 요구 사항, 워크플로, 프로젝트의 복잡성에 따라 달라집니다.



venv:

설치: Python 3.3 이상에서는 설치가 필요하지 않습니다.
Python 버전: Python 인터프리터와 동일한 버전을 사용합니다.
환경 관리: 가상 환경을 만들고, 활성화하고, 삭제하는 기본 명령어를 제공합니다.
사용 용이성: 간단하고 직관적입니다.
격리: 시스템 전체 패키지로부터 적당한 수준의 격리를 제공합니다.
종속성 관리: pip를 사용하여 관리합니다.
가상 환경:

설치: pip install virtualenv를 통해 설치해야 합니다.
Python 버전: 지정한 경우 다른 Python 버전으로 환경을 만들 수 있습니다.
환경 관리: 특정 Python 인터프리터로 환경을 만드는 등 venv에 비해 더 많은 옵션이 있습니다.
사용 편의성: venv보다 유연하지만 추가 명령이 필요합니다.
격리: 높은 격리 기능을 제공합니다.
종속성 관리: pip를 사용하여 관리합니다.
가상 환경 래퍼:

설치: pip install virtualenvwrapper를 통해 설치해야 합니다.
파이썬 버전: 환경 생성을 위해 virtualenv를 사용합니다.
환경 관리: 환경을 쉽게 만들고, 삭제하고, 환경 간에 전환할 수 있는 명령(mkvirtualenv, rmvirtualenv, workon)을 추가합니다.
사용 편의성: 여러 환경에서의 작업을 간소화합니다.
격리: 높은 격리 기능을 제공합니다.
종속성 관리: pip를 사용하여 관리합니다.
pyenv:

설치: pyenv 및 선택적으로 pyenv-virtualenv의 설치 및 설정이 필요합니다.
파이썬 버전: 여러 Python 버전을 관리하고 버전 간에 전환할 수 있습니다.
환경 관리: 고급 관리 기능으로 다양한 Python 버전과 환경 간에 원활하게 전환할 수 있습니다.
사용 편의성: 더 복잡하고 여러 도구를 통합합니다.
격리: 높은 격리 기능을 제공합니다.
종속성 관리: pip를 사용하여 관리합니다.
conda:

설치: 아나콘다 또는 미니콘다 배포가 필요합니다.
Python 버전: 여러 Python 버전을 관리하며 다양한 버전의 환경을 만들 수 있습니다.
환경 관리: 고급, 패키지 관리와 환경 관리가 하나의 도구에 포함되어 있습니다.
사용 편의성: 사용자 친화적이며, 특히 데이터 과학 워크플로우에 적합합니다.
격리: 높은 격리 기능을 제공합니다.
종속성 관리: 콘다 패키지와 pip를 사용하여 관리합니다.

poetry
사용법: 종속성을 관리하고 가상 환경을 자동으로 생성합니다.
설치: 설치: pip 또는 설치 스크립트를 통해 설치합니다.
격리: 각 프로젝트에는 고유한 환경과 종속성 트리가 있습니다.
장점:
잠금 파일로 통합 종속성 관리.
종속성을 자동으로 해결합니다.
패키지와 환경을 모두 원활하게 관리합니다.
단점:
의견 구조에 적응이 필요할 수 있습니다.
간단한 프로젝트에는 과할 수 있습니다.



<br>

<br>




<br>
<br>

[참고자료]

[DATA ON-AIR]성공적인 NoSQL 도입을 위한 키포인트 : NoSQL 데이터 모델링    
<https://dataonair.or.kr/db-tech-reference/d-lounge/technical-data/?mod=document&uid=236123>

[MongoDB] NOSQL 데이터 모델링 기법 살펴보기  
<https://velog.io/@hwaya2828/MongoDB-NOSQL-%EB%8D%B0%EC%9D%B4%ED%84%B0-%EB%AA%A8%EB%8D%B8%EB%A7%81-%EA%B8%B0%EB%B2%95-%EC%82%B4%ED%8E%B4%EB%B3%B4%EA%B8%B0>

[Wikipedia] Change data capture  
<https://en.wikipedia.org/wiki/Change_data_capture>
