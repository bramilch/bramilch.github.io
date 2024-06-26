---
layout: post
title: 파이썬 디자인 패턴과 디펜던시 인젝션 패턴 Dependency Injection Pattern
author: bramilch
date: 2024-06-14 18:00:00 +0900
categories: [Backend, Data Engineering]
tags: [Backend, Data Engineering]
pin: true
math: false
toc: true
comments: false
mermaid: false
---

<br>

> 2024/06/14: 초안 작성  
> 2024/06/25: 비교 테이블 보완, 머리말의 디자인 패턴 적용, 코드 리팩토링 관련 수정  
> 2024/06/30: 의존성 주입 패턴 추가, 

※ 내용에 오류가 있을 수 있습니다.  
※ 내용을 계속 추가, 수정, 보완하고 있습니다.  

<br>

**목차**

- [머리말](#머리말)
- [파이썬 디자인 패턴](#파이썬-디자인-패턴)
  - [생성 패턴 Creational Patterns](#생성-패턴-creational-patterns)
  - [구조 패턴 Structural Patterns](#구조-패턴-structural-patterns)
  - [행동 패턴 Behavioral Patterns](#행동-패턴-behavioral-patterns)
- [의존성 주입 패턴 DI (Dependency Injection) Pattern](#의존성-주입-패턴-di-dependency-injection-pattern)
  - [주요 개념](#주요-개념)
  - [의존성 주입 유형](#의존성-주입-유형)
  - [의존성 주입 이점](#의존성-주입-이점)
  - [Python DI 패턴 구현 예제](#python-di-패턴-구현-예제)
- [파이썬 DI 라이브러리 ***dependency\_injector***](#파이썬-di-라이브러리-dependency_injector)


<br>

## 머리말

<br>

> 현업에서 내가 직접 API를 만든다면 어떻게 만들까?

> API, 소프트웨어, 오픈소스 프로젝트들의 디자인 패턴은 어떻고, 어떻게 구현하고, 구체적인 파일 구분, 코드 흐름은 어떨까?

> 어떻게 하면 API, 소프트웨어, 오픈소스 프로젝트들의 디자인 패턴들을 빠른 시간 안에 분석하고 전체적인 구조를 파악할 수 있을까?

- 이러한 질문들의 대답을 얻기 위해 디자인 패턴 종류와 특징, 분석 방법과 팁들, 유명한 오픈소스들의 디자인 패턴과 구체적인 파일 구조, 함수, 파라미터, 코드 흐름이 어떤지, 코드 구조를 분석할 수 있는 툴들이 있는지 알아봄.

- 디자인 패턴들은 중복이 없는 정리된 패턴들. 디자인 패턴이 필요한 시점에 적용하는 것이 바람직

- 디자인 패턴 지식에 대해 많이 알고, 나의 프로그래밍 개발 실력을 뽐내기 위해 디자인 패턴을 적용하는 것은 지양

- 목적을 달성하도록 빠르게 개발하는 것을 최우선 가치로 두고, 쉬운 유지보수를 위한 중복 제거, 빠른 확장성과 기능 개선을 염두에 두며 개발하는 습관이 필요

- 코드 리팩토링의 핵심은 쉬운 유지보수를 위한 중복 제거와 기능 개선 요구 시 짧은 반영 시간을 만드는 것.


<br>

## 파이썬 디자인 패턴

<br>

- 코드 디자인 패턴은 소프트웨어 디자인 문제에 대한 검증된 솔루션

- 반복되는 디자인 문제에서 테스트되고, 재사용 가능한 솔루션, 모범 사례 best practices를 제공하여 개발 프로세스의 속도를 높일 수 있음.

- 파이썬은 다른 프로그래밍 언어와 마찬가지로 디자인 패턴을 사용하여 소프트웨어 디자인 문제를 해결

- 파이썬의 디자인 패턴은 크게 세 가지 유형으로 분류. 

***생성 패턴 Creational Patterns***

***구조 패턴 Structural Patterns***

***행동 패턴 Behavioral Patterns***

- 각 디자인 패턴은 특정 측면을 어떻게 다루느냐에 따라 구분

<br>

### 생성 패턴 Creational Patterns

<br>

- 생성 패턴은 객체 생성 메커니즘을 다루며, 상황에 적합한 방식으로 객체를 생성하는 것을 목표로 함.

- 싱글톤 Singleton: 클래스에 인스턴스가 하나만 있고 이에 대한 전역 액세스 지점 global point of access을 제공

- 팩토리 메서드 Factory Method: 객체 생성을 위한 인터페이스를 정의하지만 인스턴스화할 클래스는 서브클래스가 결정하도록 함.

- 추상 팩토리 Abstract Factory: 구체적인 클래스를 지정하지 않고 관련 또는 종속 객체 그룹(패밀리)를 생성하기 위한 인터페이스를 제공합니다.

- 빌더 Builder: 복잡한 객체들을 차례로 만듦. 객체의 구성과 표현을 분리하여 동일한 구성으로 다른 표현을 만들 수 있음.

- 프로토타입 Prototype: 프로토타입 인스턴스를 사용하여 생성할 객체의 종류를 지정하고, 프로토타입을 복사하여 새 객체를 생성

<br>

### 구조 패턴 Structural Patterns

<br>

- 구조 패턴은 클래스, 객체 구조로 구성하는 디자인 패턴. 상속하여 인터페이스를 구성하고, 단일 객체, 클라이언트별 객체 클러스터를 더 큰 구조로 결합하는 패턴

- 어댑터 Adapter: 한 클래스의 인터페이스를 클라이언트가 원하는 다른 인터페이스로 변환하여 호환되지 않는 인터페이스가 함께 작동할 수 있게 함.

- 브릿지 Bridge: 객체의 인터페이스를 구현과 분리하여 두 가지가 독립적으로 기능하도록 함.

- 컴포지트 Composite: 객체를 트리 구조로 구성하여 부분 전체 계층 구조 part-whole hierarchies를 만들고, 클라이언트가 개별 객체와 구성을 균일하게 처리할 수 있도록 함.

> part-whole hierarchies란 한 레벨에서의 객체가 관련된 객체의 다음 하위 레벨도 구성하는 구조

- 데코레이터 Decorator: 객체에 동적으로 추가 책임 additional responsibilities을 줌.

- 파사드 Facade: 복잡한 하위 시스템에 단순화된 인터페이스를 제공

> 파사드 Facade는 '얼굴'을 의미. 건축에서 외부 전면을 의미함.

<br>

### 행동 패턴 Behavioral Patterns

<br>

- 행동 패턴은 알고리즘과 객체 간의 책임 할당 the assignment of responsibilities으로 구성하는 디자인 패턴

- 책임의 연쇄 Chain of Responsibility: 객체가 요청을 처리할 때까지 잠재적인 핸들러 체인 a chain of potential handlers을 따라 요청을 전달

- 명령 Command: 요청을 객체로 캡슐화하여 사용자가 큐, 요청 및 오퍼레이션 operations으로 클라이언트를 매개변수화할 수 있도록 함.

- 인터프리터 Interpreter: 복합 구조 문법에 대한 인터프리터를 제공

- 이터레이터 Iterator: 기본 표현을 노출하지 않고 객체를 모아 요소에 순차적으로 액세스할 수 있는 방법을 제공

- 매개자 Mediator: 객체로 객체들 간 상호작용들을 캡슐화하여 정의

- 메멘토 Memento: 객체의 상태를 캡처하고 내재화해서 객체의 특정한 상태로 복원

- 관찰자 Observer: 객체 간의 일대다 의존성을 정의하여, 한 객체의 상태가 변경되면, 모든 종속체에 알림이 전송되고 자동으로 업데이트되도록 함.

- 상태 State: 내부 상태가 변경될 때 객체의 동작을 변경함.

- 전략 Strategy: 알고리즘들을 정의하고 각 알고리즘을 캡슐화하여 상호 교환할 수 있도록 함.

- 템플릿 메서드 Template Method: Operation에서 알고리즘의 핵심을 정의하고, 일부 단계를 하위 클래스로 나중에 정의함.

- 방문자 Visitor: 객체 구조 요소들의 Operation을 나타냄.


<br>

<center><span style="font-size:1.2em;"> 파이썬 디자인 패턴 비교</span></center>

<br>

|카테고리| 패턴 |설명|
|------------------|-------------------|------------------------|
|생성|싱글톤 Singleton|클래스에 인스턴스가 하나만 있도록 하고 전역 액세스 포인트를 제공|
|생성|팩토리 메서드 Factory Method|객체를 생성하기 위한 인터페이스를 정의하지만 서브클래스가 인스턴스화할 클래스를 결정할 수 있도록 함.|
|생성|추상 팩토리 Abstract Factory|구체적인 클래스를 지정하지 않고 관련 또는 종속 객체의 패밀리를 생성하기 위한 인터페이스를 제공|
|생성|빌더 Builder|복잡한 객체의 구성과 그 표현을 분리|
|생성|프로토타입 Prototype|프로토타입 인스턴스를 사용하여 생성할 객체의 종류를 지정하고 이 프로토타입을 복사하여 새 객체를 생성|
|구조|어댑터 Adapter|한 클래스의 인터페이스를 클라이언트가 기대하는 다른 인터페이스로 변환|
|구조|브릿지 Bridge|추상화와 구현을 분리하여 두 가지가 독립적으로 변할 수 있도록 함.|
|구조|합성 Composite|객체를 트리 구조로 구성하여 부분 전체 계층 구조를 나타냄.|
|구조|데코레이터 Decorator|오브젝트에 동적으로 추가 책임을 부여|
|구조|파사드 Facade|하위 시스템의 인터페이스 세트에 통합된 인터페이스를 제공|
|동작|책임 연쇄 패턴 Chain of Responsibility|연쇄적인 객체가 요청을 처리할 때까지 연쇄적인 잠재 핸들러 potential handlers가 요청을 전달|
|동작|명령 Command|요청을 객체로 캡슐화하여 유저가 큐, requests, 연산 operations으로 클라이언트를 매개변수화할 수 있도록 함.|
|동작|인터프리터 Interpreter|복합 구조로 표현되는 문법에 대한 인터프리터를 제공|
|동작|이터레이터	Iterator|집합 객체의 요소에 순차적으로 액세스하는 방법을 제공|
|동작|매개자 Mediator|객체 집합끼리 상호 작용하는 방식을 캡슐화한 객체를 정의|
|동작|메멘토 Memento|객체를 특정 상태로 복원할 수 있도록 객체의 상태를 캡처하고 내재화 Internalizing|
|동작|관찰자 Observer|객체 간의 일대다 의존성을 정의하여 한 객체의 상태가 변경되면 모든 종속 객체에 알림이 전송되고 자동으로 업데이트되도록 함.|
|동작|상태 State|내부 상태가 변경되면 객체의 동작이 변경되도록 함.|
|동작|전략 Strategy|알고리즘들을 정의하고, 각 알고리즘을 캡슐화하여 상호 교환 가능하게 함.|
|동작|템플릿 메서드 Template Method|연산에서 알고리즘의 골격을 정의하여 일부 단계를 하위 클래스에서 다루도록 함.|
|동작|방문자 Visitor|객체 구조의 요소들에 대해 수행될 연산을 나타냄.|

<br>

## 의존성 주입 패턴 DI (Dependency Injection) Pattern

<br>

- 의존성 주입 패턴 Dependency Injection (DI) Pattern은 클래스와 해당 의존성 간에 ***제어의 역전 Inversion of Control (IoC)***을 달성 목표

- 클래스 내에서 디펜던시(의존성)를 만드는 대신 일반적으로 생성자, 세터 setters 또는 인터페이스를 통해 외부 소스에서 클래스에 의존성을 주입함. 이렇게 하면 느슨한 결합, 더 쉬운 테스트 및 더 나은 유지 관리가 가능

<br>

### 주요 개념

<br>

- 제어의 역전 **Inversion of Control (IoC)**: 의존성을 생성하고 관리하는 제어권이 종속 클래스에서 외부 프레임워크 또는 컨테이너로 반전

- 의존성 주입**Dependency Injection (DI)**: 클래스에서 의존성을 생성하는 대신 의존성을 클래스에 제공하는 IoC를 구현하는 방법.

<br>

### 의존성 주입 유형

<br>

- 생성자 주입 **Constructor Injection**: 클래스 생성자를 통해 의존성을 제공합니다.

- 세터 주입 **Setter Injection**: 세터 메서드를 통해 의존성을 제공합니다.

- 인터페이스 주입 **Interface Injection**: 의존성은 인터페이스를 통해 제공됩니다(파이썬에서는 덜 일반적임).

<br>

### 의존성 주입 이점

<br>

- 느슨한 결합 **Loose Coupling**: 클래스가 의존성에 단단히 묶여 있지 않으므로 시스템이 더 모듈화됩니다.

- 테스트의 용이성 **Ease of Testing**: 단위 테스트 중에 의존성을 쉽게 모킹하거나 스텁할 수 있습니다.

- 유연성 및 재사용성 **Flexibility and Reusability**: 구성 요소는 다양한 구성과 의존성으로 재사용할 수 있습니다.

<br>

### Python DI 패턴 구현 예제

<br>

1. 인터페이스/프로토콜을 정의합니다: 의존성에 필요한 동작을 지정합니다.

```
from abc import ABC, abstractmethod

class Database(ABC):
    @abstractmethod
    def query(self, sql: str):
        pass
```


2. 구체적인 클래스 구현: 의존성에 대한 구체적인 구현을 제공합니다.

```
class MySQLDatabase(Database):
    def query(self, sql: str):
        return f"Executing '{sql}' on MySQL"

```

3. 생성자를 통해 의존성 주입: 클래스 생성자를 통해 의존성을 전달합니다.

```
class Service:
    def __init__(self, db: Database):
        self.db = db

    def get_data(self, sql: str):
        return self.db.query(sql)
```


4. 의존성 어셈블리: 인스턴스를 생성하고 의존성을 주입합니다.

```
db = MySQLDatabase()
service = Service(db)
result = service.get_data("SELECT * FROM users")
print(result)
```


- 인터페이스 분리: 인터페이스를 사용하여 의존성의 예상 동작을 정의

- 단일 책임 **Single Responsibility**: 각 클래스는 단일 책임을 가져야 함.

- DI 컨테이너 사용: 대규모 프로젝트에서 의존성을 관리하려면 DI 프레임워크 또는 컨테이너(예: dependency_injector 라이브러리)를 사용하는 것이 유리

<br>

## 파이썬 DI 라이브러리 ***dependency_injector***

<br>


<br>
<br>

[참고자료]

[GeeksforGeeks] Python Design Patterns  
<https://www.geeksforgeeks.org/python-design-patterns/>