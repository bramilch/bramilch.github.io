---
layout: post
title: 웹 프레임워크 종류, 비교와 선택
author: bramilch
date: 2024-05-21 18:00:00 +0900
categories: [Backend, Data Engineering]
tags: [Backend, Data Engineering]
pin: true
math: false
toc: true
comments: false
mermaid: false
image:
  path: ./assets/img/posts/2024-05-21-kr-web-framework-comparing/web-frameworks-imagesjpg.jpg
---

<br>

> 2024/05/21: 초안 작성  
> 2024/05/23: 각 언어별 웹프레임워크 테이블 추가  
> 2024/05/24: Spring, Django, Flask 비교 추가
> 2024/05/24: 웹 프레임워크 선택 기준, 구체적인 웹 프레임워크들 장단점 추가, 보완

※ 내용에 오류가 있을 수 있습니다.  
※ 내용을 계속 추가, 수정, 보완하고 있습니다.  

<br>

**목차**

- [머리말](#머리말)
- [웹 프레임워크 선택의 문제](#웹-프레임워크-선택의-문제)
- [프론트엔드 웹 프레임워크 Front-End Web Frameworks](#프론트엔드-웹-프레임워크-front-end-web-frameworks)
- [백엔드 웹 프레임워크 Back-End Web Frameworks](#백엔드-웹-프레임워크-back-end-web-frameworks)
- [풀스택 웹 프레임워크 Full-Stack Web Frameworks](#풀스택-웹-프레임워크-full-stack-web-frameworks)

<br>

## 머리말

<br>

- 웹 개발을 하려고 할 때, 제로 코드에서 스스로 모든 것을 개발하기엔 시간, 개인, 팀이 투입하는 노력, 비용이 너무 큼.

- 정확히는 웹 개발을 위한 웹 개발 프레임워크(WF, Web Framework), 웹 애플리케이션 프레임워크(WAF, Web Application Framework)로서, 프론트엔드 웹 프레임워크 Front-End Web Frameworks, 백엔드 웹 프레임워크 Back-End Web Frameworks, 풀스택 웹 프레임워크 Full-Stack Web Frameworks가 있음.

-  이미 많은 사람들이 웹 개발을 위한 반제품처럼 웹 프레임워크를 만들어놓았고 ~~무료, 오픈소스로, 감사하게도!~~, 프로젝트에 맞게 선택, 수정, 조합해서 쓰면 됨.

- 다만 프론트엔드, 백엔드, 풀스택으로 웹 프레임워크를 구분할 수 있고, 한 가지 프레임워크가 내가 원하는 기능들을 모두 커버할 수 있지 않을 확률이 높기 때문에 선택, 조합을 위해 특성, 장단점, 비교 등 충분한 고려가 필요함.

- 또 각 웹 프레임워크는 각각의 아키텍처를 갖기 때문에 학습에 시간, 노력이 필요하기 때문에 전략적인 선택이 중요함.

- 내가 서비스를 구현하고자 할 때 웹 개발 프레임워크에서  가장 고민했던 것은 한국의 전자정부 표준 프레임워크이자 가장 널리 쓰이는 Java 기반의 Spring과 Python 기반의 Django, Flask 중 무엇을 선택해야 할까였음.

- 프론트엔드, 백엔드 및 풀스택 웹 프레임워크는 웹 개발의 필수 구성 요소로, 각각 고유한 역할을 수행하며 웹 애플리케이션의 전반적인 기능과 모양 결정지을 수 있음. 이러한 ***프레임워크 간의 차이점과 유사점을 이해하는 것은 특정 프로젝트에 어떤 기술을 사용할지 정보에 입각한 결정을 내리는 데 매우 중요함.***

- 우선 Java와 Python 기반의 웹 개발 프레임워크에 대해서 알아보고자 함.

<br>

## 스프링 Spring, 장고 Django, 플라스크 Flask 비교

<br>

**정리**

- 스프링 Spring: 고성능과 확장성이 필요한 복잡한 엔터프라이즈급 애플리케이션에 가장 적합

- Django: Robust하고 모든 기능을 갖춘 프레임워크로 빠른 개발에 가장 적합

- Flask: 유연성과 단순성이 필요한 중소규모 애플리케이션에 가장 적합

<br>

<details><summary> 웹에서 Robust란 의미 </summary><div markdown="1">

<br>  

robust
_adjective_
1. strong and healthy; vigorous.
2. (of wine or food) strong and rich in flavor or smell.
from Google Dictionary
	
> "Robustness, as defined by WCAG, refers specifically to **web content that is compatible with a variety of “user agents”: browsers, assistive technologies, and other means of accessing web content**." by [WCAG 2.1 Principles Explained: Robustness](https://www.boia.org/blog/wcag-2.1-principles-explained-robustness#:~:text=Robustness%2C%20as%20defined%20by%20WCAG,means%20of%20accessing%20web%20content.)

> "Ensure your site looks and functions seamlessly on various screen sizes."

> "견고성(Robust) : 웹 콘텐츠는 미래의 기술로도 접근할 수 있도록 견고하게 만들어야 한다." 
> - 문법 준수(마크업 오류 방지): 마크업 언어의 요소는 열고 닫음, 중첩 관계 및 속성 선언에 오류가 없어야 한다.
> - 웹 애플리케이션 접근성|(웹 애플리케이션 접근성 준수): 콘텐츠에 포함된 웹 애플리케이션은 접근성이 있어야 한다.  
> by [문화체육관광부 국립장애인도서관 (웹 및 모바일) 접근성](https://www.nld.go.kr/ableFront/new_standard_guide/accessibility.jsp)

</div></details>



<br>
<center><span style="font-size:1.2em;">Spring과 Django, Flask 비교</span></center>

<br>

|기능/기준|**스프링(Java)**|**장고(파이썬)**|**플라스크(파이썬)**|
|---|---|---|---|
|**언어**| 자바 |파이썬| 파이썬|
|**아키텍처**|모든 기능을 갖춘 프레임워크(Full-featured framework), MVC |모든 기능을 갖춘 프레임워크, MVT |마이크로 프레임워크, WSGI|
|**성능**|고성능 및 확장성| 우수한 성능, 그러나 대규모 앱의 경우 Spring보다 느릴 수 있음 |경량, 적절한 최적화를 통해 고성능 구현 가능|
|**사용 용이성**| 가파른 학습 곡선, 광범위한 구성 |"배터리 포함 batteries-included" 철학으로 사용하기 쉬움 |매우 사용하기 쉽고, 미니멀한 디자인|
|**유연성**|매우 유연함, 광범위한 사용자 지정| 적당히 유연함, 구성에 대한 관습| 매우 유연함, 제한 최소화|
|**커뮤니티 지원**|대규모의 성숙한 커뮤니티| 대규모의 활발한 커뮤니티 |대규모의 활발한 커뮤니티|
|**라이브러리 및 플러그인**|광범위한 에코시스템, 다양한 플러그인 지원| 광범위한 기본 제공 모듈 및 타사 패키지 다양한 확장 기능 사용 가능|
|**보안**| 높음, 많은 내장 보안 기능| 높음, 많은 내장 보안 기능 사용| 확장 기능에 따라 다름|
|**개발 속도**|복잡성 및 구성으로 인해 느림 |기본 제공 기능으로 빠른 개발 |단순성으로 인해 가장 빠름|
|**적합한 프로젝트**|대규모 엔터프라이즈급 애플리케이션에 적합 |강력한 robust 웹 애플리케이션의 빠른 개발| 경량 애플리케이션, 마이크로 서비스|
|**제한 사항**|소규모 프로젝트에는 과할 수 있음| 모놀리식 monolithic이 될 수 있으며 Flask보다 유연성이 떨어짐 |기본 제공 기능이 제한적이며 확장 기능에 의존함|
|**장점**|고성능|빠른 개발|간단하고 가벼움|
||확장 가능|사용하기 쉬움|유연함|
||성숙하고 안정적|훌륭한 커뮤니티 및 문서|마이크로서비스 및 소규모 앱에 적합|
|단점|가파른 학습 곡선|대규모 앱의 경우 속도가 느릴 수 있음|대규모 모놀리식 앱에는 적합하지 않음|
||더 복잡한 설정|Flask보다 유연성이 떨어짐|기본 제공 기능이 적음|







<br>

<center><span style="font-size:1.2em;">언어별 웹 프레임워크 정리</span></center>

<br>

|주요 사용 언어|프레임워크 이름|설명|
|---|---|---|---|
|**JavaScript**|React|사용자 인터페이스, 특히 단일 페이지 애플리케이션을 구축하기 위한 자바스크립트 리액트 라이브러리|
||Angular|웹 애플리케이션 구축을 위한 Full-fledged framework|
||Vue.js|사용자 인터페이스 구축을 위한 Progressive framework|
||Express.js|최소한의 유연성을 강조 Node.js 웹 애플리케이션 프레임워크|
|**Python**|Django|빠른 개발과 깔끔하고 실용적인 디자인을 장려하는 Python 웹 풀스택 프레임워크|
||Flask|Python으로 작성된 Flask Micro 웹 프레임워크|
|**PHP**|Laravel|PHP Laravel MVC 아키텍처 패턴을 따르는 PHP 프레임워크|
||Symfony|웹 애플리케이션 및 서비스를 위한 Symfony PHP 프레임워크|
|**Java**|Spring Boot|독립형 프로덕션급 Spring 기반 애플리케이션을 구축하기 위한 Java Spring Boot Java 기반 프레임워크|
||Struts|엔터프라이즈급 Java 웹 애플리케이션을 제작하기 위한 오픈 소스 프레임워크|
|**Ruby**|Ruby on Rails|구성보다 규칙을 강조하는 Ruby on Rails Ruby 프레임워크|
||Sinatra|Ruby로 웹 애플리케이션을 빠르게 제작하기 위한 Sinatra DSL|
|**.NET**|ASP.NET Core|클라우드 기반 인터넷 연결 애플리케이션을 빌드하기 위한 고성능 오픈 소스 프레임워크인 .NET ASP.NET Core 크로스 플랫폼|
|**Go**|Gin|Go(Golang)로 작성된 Go Gin HTTP 웹 프레임워크|
|**Node.js**|Koa|Node.js Koa 웹 애플리케이션 및 API를 구축하기 위한 표현력이 풍부하고 강력하며 유연한 프레임워크|
|**Rust**|Rocket|빠르고 안전한 웹 애플리케이션을 간편하게 작성할 수 있는 Rust용 Rust Rocket 웹 프레임워크|
|**Swift**|Vapor|Swift Vapor 웹 애플리케이션 구축을 위한 Swift 웹 프레임워크|
|**TypeScript**|NestJS|F효율적이고 확장 가능한 Node.js 서버 측 애플리케이션을 구축하기 위한 TypeScript NestJS 프레임워크|
|**C#**|ASP.NET MVC|웹 애플리케이션 구축을 위한 C# ASP.NET MVC 모델-뷰-컨트롤러 프레임워크|
|**Scala**|Play|Scala Play Java 및 Scala용 고속 웹 프레임워크|
|**Elixir**|Phoenix|고성능 웹 애플리케이션 구축을 위해 구축된 Elixir Phoenix 웹 프레임워크|
|**Kotlin**|Ktor|Kotlin을 사용하여 연결된 시스템에서 비동기 서버 및 클라이언트를 빌드하기 위한 Kotlin Ktor 프레임워크|
|**Julia**|Genie.jl|웹 애플리케이션 빌드를 위한 Julia 패키지|
|**R**|Shiny|대화형 웹 애플리케이션을 빌드하기 위한 R Shiny R 패키지|

<br>

## 웹 프레임워크 선택의 문제

- 프론트엔드, 백엔드, 풀스택 프레임워크 중 어떤 것을 선택할지는 ***프로젝트의 구체적인 요구 사항(필요 기술, 확장성과 연관)***, 팀의 전문성(개발 역량, 주어진 리소스와 제한된 시간 등), 애플리케이션의 장기적인 목표(확장성과도 연관)에 따라 달라짐. 

**프로젝트 요구 사항 Project Requirements**
- 프로젝트의 구체적인 요구 사항, 규모, 복잡성을 결정하는 것이 필수. 예를 들어 실시간 애플리케이션을 구축하는 경우 WebSocket 통신을 지원하는 프레임워크가 유용할 수 있음.   필요한 특정 기능(예: 실시간 업데이트, 대용량 데이터 처리)을 고려하는 것이 필수


**개발 속도 vs 제어 Development Speed vs. Control**
- 제품을 빠르게 출시해야 하는 경우 내장된 기능을 갖춘 장고나 레일즈와 같은 프레임워크가 시간을 절약할 수 있음.
- 컴포넌트에 대한 더 많은 제어가 필요하다면 Flask나 Express.js와 같은 마이크로 프레임워크가 더 적합할 수 있음.


**학습 곡선 Learning Curve**
- 각 프레임워크에는 고유한 규칙과 관행이 있으므로 학습에 시간이 필요함.

**성능 및 확장성 Performance and Scalability**
- 프레임워크는 추상화 계층으로 인해 성능 오버헤드가 발생할 수 있지만, 많은 프레임워크가 모듈식 아키텍처를 통해 확장성을 지원
- 성능 요구 사항 Performance Needs에서 고성능 및 확장성 애플리케이션은 Spring 또는 ASP.NET Core와 같은 프레임워크가 유용할 수 있고, 빠른 개발과 유연성이 필요한 경우에는 Django 또는 Flask가 적합할 수 있음.


**신속한 개발 Rapid Development**
- 웹 프레임워크는 사전 빌드된 구성 요소를 제공하여 개발 프로세스의 속도를 높임.

**에코시스템 및 커뮤니티 지원 Ecosystem and Community Support**
- 강력한 커뮤니티 지원과 라이브러리 및 도구 에코시스템을 갖춘 프레임워크를 선택할 필요. 문제 해결과 애플리케이션의 기능 확장에 도움이 될 수 있음.


## 프론트엔드 웹 프레임워크 Front-End Web Frameworks

<br>

- 웹 애플리케이션의 사용자 인터페이스와 사용자 경험에 중점을 둠 사용자가 브라우저에서 보고 상호 작용하는 내용을 구성함.

- 기술: HTML, CSS, JavaScript는 프론트엔드 개발을 위한 기본 기술. 이러한 기술을 확장하여 UI 사용자 인터페이스를 보다 효율적이고 체계적으로 구축할 수 있는 방법을 제공하는 인기 있는 프레임워크에는 React, Angular, Vue.js 등이 있음.

- 프레임워크 및 라이브러리: 부트스트랩 Bootstrap과 파운데이션 Foundation은 웹 페이지를 구조화하고 스타일을 지정하는 데 널리 사용됨. 개발자가 동적이고 반응이 빠른 사용자 인터페이스를 만들 수 있는 JavaScript 프레임워크/라이브러리인 React, Angular, Vue.js가 있음.

- 학습의 용이성: 프론트엔드 개발은 서버 측 프로그래밍의 복잡성 없이 시각적 요소와 사용자 상호작용을 주로 다루기 때문에 일반적으로 초기에 배우기 쉬움.

<br>

## 백엔드 웹 프레임워크 Back-End Web Frameworks

<br>


- 웹 애플리케이션의 서버 측 로직과 관련이 있습니다. 데이터 처리, 비즈니스 로직, 데이터베이스와의 상호 작용을 처리

- 기술: 일반적인 백엔드 언어에는 PHP, Ruby, Python, Node.js 등이 있습니다. Ruby on Rails, Laravel, Django와 같은 프레임워크는 애플리케이션을 구축하기 위한 구조와 도구를 제공

- 프레임워크 및 라이브러리: Express.js는 웹 애플리케이션과 API를 구축하는 데 널리 사용되는 미니멀리즘 Node.js 프레임워크임. 다른 주목할 만한 백엔드 프레임워크로는 ASP.NET Core for.NET 애플리케이션과 Java 애플리케이션용 Spring Boot가 있음.

- 복잡성 및 제어: 백엔드 개발은 더 복잡하고 서버 및 데이터베이스 관리에 대한 더 많은 제어 기능을 제공. 따라서 서버 측 프로그래밍 및 데이터베이스 관리 시스템에 대한 깊은 이해가 필요함.

<br>

## 풀스택 웹 프레임워크 Full-Stack Web Frameworks

<br>

- 프론트엔드 및 백엔드 개발을 모두 포함하므로 개발자가 웹 애플리케이션의 모든 측면에서 작업할 수 있음.

- 기술: 풀스택 프레임워크는 프론트엔드 및 백엔드 개발의 기술을 결합하는 경우가 많습니다. 예를 들어 MEAN/MERN 스택(MongoDB, Express.js, Angular/React, Node.js)과 LAMP/LNMP 스택(Linux, Apache/Nginx, MySQL/PostgreSQL, PHP/Python/Perl)이 있음.

- 프레임워크 및 라이브러리: MEAN/MERN과 같은 풀스택 프레임워크는 통합된 개발 환경을 제공하여 개발자가 JavaScript를 사용하여 전체 애플리케이션 스택에서 원활하게 작업할 수 있도록 지원함.

- 다양성 및 효율성: 풀스택 개발은 개발 프로세스를 간소화하고 효율성을 높일 수 있다는 점에서 높은 평가를 받고 있음. 이를 통해 개발자는 프레젠테이션 계층과 기본 로직을 모두 이해하고 작업할 수 있으므로 애플리케이션을 전체적으로 파악할 수 있음.

## 구체적인 웹 개발 프레임워크들의 장단점

----
1. **Django (Python)**
2. **Flask (Python)**
3. **Spring (Java)**
4. **Express.js (JavaScript)**
5. **Ruby on Rails (Ruby)**
6. **Laravel (PHP)**
7. **ASP.NET Core (C#)**
8. **Vue.js/Nuxt.js (JavaScript)**
9. **React.js/Next.js (JavaScript)**
10. **Angular (JavaScript/TypeScript)**

-----

<br>

### 1. Django (Python)

**특징**
- MVT(모델-뷰-템플릿) 아키텍처 패턴을 따르는 모든 기능을 갖춘 높은 수준의 Python 프레임워크입니다.

**장점**
- 기본 제공 기능으로 신속한 개발이 가능합니다.
- 강력한 커뮤니티와 방대한 문서.
- 뛰어난 보안 기능.
- 대규모 애플리케이션을 위한 확장성.

**단점**
- 마이크로 프레임워크에 비해 모놀리식이며 유연성이 떨어질 수 있습니다.
- 소규모 프로젝트에는 과할 수 있습니다.

**주의 사항**
- 불필요한 복잡성을 피하기 위해 프로젝트의 규모가 장고 사용을 정당화할 수 있는지 확인하세요.

### 2. Flask (Python)

**특징**
- 필수 기능을 제공하고 유연성을 높여주는 가벼운 파이썬용 마이크로 프레임워크입니다.

**장점**
- 매우 유연하고 사용하기 쉽습니다.
- 미니멀리즘으로 맞춤형 구현이 가능합니다.
- 중소규모 애플리케이션 및 마이크로서비스에 적합합니다.

**단점**
- 기본 제공 기능이 부족하며 추가 기능을 위해 확장 프로그램이 필요합니다.
- 대규모의 복잡한 애플리케이션에는 적합하지 않으며 사용자 정의가 필요하지 않습니다.

**주의 사항**
- 종속성을 주의 깊게 관리하고 필요한 보안 기능을 추가해야 합니다.

### 3. Spring (Java)

**특징**
- Java로 엔터프라이즈급 애플리케이션을 구축하기 위한 포괄적인 프레임워크로, MVC(모델-뷰-컨트롤러) 패턴을 따릅니다.

**장점**
- 높은 성능과 확장성.
- 강력한 보안 기능.
- 수많은 모듈과 확장 기능을 갖춘 광범위한 에코시스템.

**단점**
- 가파른 학습 곡선.
- 설정 및 구성이 더 복잡합니다.

**주의 사항**
- 복잡성이 부담스러울 수 있으므로 팀이 Java에 능숙하고 Spring에 익숙한지 확인하세요.

### 4. Express.js (JavaScript)

**특징**
- 의견에 구애받지 않고 유연하게 사용할 수 있는 미니멀리즘 웹 프레임워크입니다.

**장점**
- 가볍고 빠릅니다.
- 방대한 에코시스템(npm)으로 매우 유연합니다.
- 실시간 애플리케이션에 탁월합니다.

**단점**
- 미니멀리즘 특성상 수동으로 기능을 추가해야 합니다.
- 일관성 없는 코드 구조로 이어질 수 있습니다.

**주의 사항**
- 팀 전체에서 일관된 코딩 관행과 구조를 유지하세요.

### 5. Ruby on Rails (Ruby)

**특징**
- Ruby를 위한 풀스택 프레임워크로, MVC 패턴을 따르며 구성보다 규칙을 강조합니다.

**장점**
- 규칙 기반 접근 방식으로 신속한 개발이 가능합니다.
- 대규모 커뮤니티와 좋은 문서.
- 다양한 기본 제공 도구 및 라이브러리 세트.

**단점**
- 부하가 매우 높은 애플리케이션의 경우 성능이 저하될 수 있습니다.
- 규칙으로 인해 유연성이 떨어집니다.

**주의 사항**
- 애플리케이션의 성능 요구 사항을 평가하여 Rails가 부하를 처리할 수 있는지 확인하세요.

### 6. Laravel (PHP)

**특징**
- MVC 패턴을 따르는 우아하고 모든 기능을 갖춘 PHP 프레임워크입니다.

**장점**
- 깔끔한 구문으로 개발자 친화적입니다.
- 광범위한 기본 제공 기능 및 패키지.
- 강력한 커뮤니티와 훌륭한 문서.

**단점**
- 매우 큰 규모의 애플리케이션에서는 성능이 문제가 될 수 있습니다.
- 일부 개발자 커뮤니티에서는 PHP 자체의 인기가 떨어집니다.

**주의할 점**
- 확장성을 위해 성능을 모니터링하고 쿼리를 최적화하세요.

### 7. ASP.NET Core (C#)

**특징**
- 최신 클라우드 기반 웹 애플리케이션을 구축하기 위한 크로스 플랫폼 고성능 프레임워크입니다.

**장점**
- 고성능 및 확장성.
- 보안 및 인증에 대한 강력한 지원.
- 엔터프라이즈급 애플리케이션에 적합합니다.

**단점**
- C# 및 .NET 에코시스템에 대한 지식이 필요합니다.
- 설정 및 구성이 복잡할 수 있습니다.


**주의 사항**
- 팀이 Microsoft 스택 및 .NET Core 환경에 익숙한지 확인하세요.

### 8. Vue.js/Nuxt.js (JavaScript)

**특징**
-사용자 인터페이스를 구축하기 위한 프로그레시브 자바스크립트 프레임워크로, 서버 측 렌더링으
로 Vue.js를 확장한 Nuxt.js입니다.

**장점**
- 반응형 및 컴포넌트 기반 아키텍처.
- 배우기 쉽고 통합하기 쉽습니다.
- 단일 페이지 애플리케이션(SPA)에 적합합니다.

**단점**
- React에 비해 제한된 에코시스템.
- 간단한 애플리케이션에는 과할 수 있습니다.


**주의 사항**
- Nuxt.js의 복잡성이 프로젝트 요구 사항과 일치하는지 확인하세요.

### 9. React.js/Next.js (JavaScript)

**특징**
- 서버 측 렌더링 및 정적 사이트 생성을 위한 프레임워크로 사용자 인터페이스(React)를 구축하기 위한 라이브러리(Next.js).

**장점**
- 높은 성능과 유연성.
- 대규모 커뮤니티와 광범위한 에코시스템.
- 복잡한 SPA 및 동적 웹 애플리케이션에 적합합니다.

**단점**
- 초보자를 위한 가파른 학습 곡선.
- 적절한 구조화 없이 상용구 코드가 생성될 수 있습니다.

**주의 사항**
- 복잡성을 피하기 위해 상태를 적절히 관리하고 최적의 구조화를 보장하세요.

### 10. Angular (JavaScript/TypeScript)

**특징**
- Google에서 개발한 동적 웹 애플리케이션 구축을 위한 본격적인 프레임워크입니다.

**장점**
- 프론트엔드 개발에 필요한 모든 것을 갖춘 포괄적인 솔루션.
- 대규모 애플리케이션 구축을 위한 강력한 지원.
- 타입스크립트 지원으로 타입 안전성이 추가되었습니다.

**단점**
- 가파른 학습 곡선.
- 소규모 프로젝트에는 과할 수 있습니다.


**주의 사항**
- 프로젝트 규모와 복잡성이 Angular의 사용을 정당화할 수 있는지 확인하세요.



## 참고자료

- [문화체육관광부 국립장애인도서관 (웹 및 모바일) 접근성]<https://www.nld.go.kr/ableFront/new_standard_guide/accessibility.jsp>
-  [WCAG 2.1 Principles Explained: Robustness]<https://www.boia.org/blog/wcag-2.1-principles-explained-robustness#:~:text=Robustness%2C%20as%20defined%20by%20WCAG,means%20of%20accessing%20web%20content>
