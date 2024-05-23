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

- 또 각 웹 프레임워크는 각각의 아키텍처를 갖기 때문에 학습에 시간, 노력이 필요함.

- 프론트엔드, 백엔드 및 풀스택 웹 프레임워크는 웹 개발의 필수 구성 요소로, 각각 고유한 역할을 수행하며 웹 애플리케이션의 전반적인 기능과 모양 결정지을 수 있음. 이러한 ***프레임워크 간의 차이점과 유사점을 이해하는 것은 특정 프로젝트에 어떤 기술을 사용할지 정보에 입각한 결정을 내리는 데 매우 중요함.***

<br>

언어별 웹 프레임워크 정리

|주요 사용 언어|프레임워크 이름|설명|웹사이트|
|---|---|---|---|
|**JavaScript**|React|사용자 인터페이스, 특히 단일 페이지 애플리케이션을 구축하기 위한 자바스크립트 리액트 라이브러리 |[React](https://reactjs.org/)|
||Angular|웹 애플리케이션 구축을 위한 Full-fledged framework|[Angular](https://angular.io)|
||Vue.js|사용자 인터페이스 구축을 위한 Progressive framework|[Vue.js](https://vuejs.org)|
||Express.js|최소한의 유연성을 강조 Node.js 웹 애플리케이션 프레임워크|[Express.js](http://expressjs.com)|
|**Python**|Django|빠른 개발과 깔끔하고 실용적인 디자인을 장려하는 Python 웹 풀스택 프레임워크|[Django](https://www.djangoproject.com)|
||Flask|Python으로 작성된 Flask Micro 웹 프레임워크|[Flask](https://flask.palletsprojects.com/en/2.0.x)|
|**PHP**|Laravel|PHP Laravel MVC 아키텍처 패턴을 따르는 PHP 프레임워크|[Laravel](https://laravel.com)|
||Symfony|웹 애플리케이션 및 서비스를 위한 Symfony PHP 프레임워크|[Symfony](https://symfony.com)|
|**Java**|Spring Boot|독립형 프로덕션급 Spring 기반 애플리케이션을 구축하기 위한 Java Spring Boot Java 기반 프레임워크|[Spring Boot](https://spring.io/projects/spring-boot)|
||Struts|엔터프라이즈급 Java 웹 애플리케이션을 제작하기 위한 오픈 소스 프레임워크|[Struts](https://struts.apache.org)|
|**Ruby**|Ruby on Rails|구성보다 규칙을 강조하는 Ruby on Rails Ruby 프레임워크|[Ruby on Rails](https://rubyonrails.org)|
||Sinatra|Ruby로 웹 애플리케이션을 빠르게 제작하기 위한 Sinatra DSL|[Sinatra](http://sinatrarb.com)|
|**.NET**|ASP.NET Core|클라우드 기반 인터넷 연결 애플리케이션을 빌드하기 위한 고성능 오픈 소스 프레임워크인 .NET ASP.NET Core 크로스 플랫폼|[.NET](https://dotnet.microsoft.com/apps/aspnet)|
|**Go**|Gin|Go(Golang)로 작성된 Go Gin HTTP 웹 프레임워크|[Gin](https://github.com/gin-gonic/gin)|
|**Node.js**|Koa|Node.js Koa 웹 애플리케이션 및 API를 구축하기 위한 표현력이 풍부하고 강력하며 유연한 프레임워크|[Koa](https://koajs.com)|
|**Rust**|Rocket|빠르고 안전한 웹 애플리케이션을 간편하게 작성할 수 있는 Rust용 Rust Rocket 웹 프레임워크|[Rocket](https://rocket.rs)|
|**Swift**|Vapor|Swift Vapor 웹 애플리케이션 구축을 위한 Swift 웹 프레임워크|[Vapor](https://vapor.codes)|
|**TypeScript**|NestJS|F효율적이고 확장 가능한 Node.js 서버 측 애플리케이션을 구축하기 위한 TypeScript NestJS 프레임워크|[NestJS](https://nestjs.com)|
|**C#**|ASP.NET MVC|웹 애플리케이션 구축을 위한 C# ASP.NET MVC 모델-뷰-컨트롤러 프레임워크|[.NET MVC](https://docs.microsoft.com/en-us/aspnet/mvc/overview/getting-started/introduction/creating-a-new-project-in-an-existing-solution)|
|**Scala**|Play|Scala Play Java 및 Scala용 고속 웹 프레임워크|[Play](https://www.playframework.com)|
|**Elixir**|Phoenix|고성능 웹 애플리케이션 구축을 위해 구축된 Elixir Phoenix 웹 프레임워크|[Phoenix](https://hexdocs.pm/phoenix/readme.html)|
|**Kotlin**|Ktor|Kotlin을 사용하여 연결된 시스템에서 비동기 서버 및 클라이언트를 빌드하기 위한 Kotlin Ktor 프레임워크|[Ktor](https://ktor.io)|
|**Julia**|Genie.jl|웹 애플리케이션 빌드를 위한 Julia 패키지|[Genie.jl](https://genie.juliadata.org)|
|**R**|Shiny|대화형 웹 애플리케이션을 빌드하기 위한 R Shiny R 패키지|[Shiny](https://shiny.rstudio.com)|

<br>

## 웹 프레임워크 선택의 문제

- 프론트엔드, 백엔드, 풀스택 프레임워크 중 어떤 것을 선택할지는 프로젝트의 구체적인 요구 사항(필요 기술, 확장성과 연관), 팀의 전문성(개발 역량, 주어진 리소스와 제한된 시간 등), 애플리케이션의 장기적인 목표(확장성과도 연관)에 따라 달라짐. 

- 학습 곡선 Learning Curve: 각 프레임워크에는 고유한 규칙과 관행이 있으므로 학습에 시간이 필요함.

- 성능 및 확장성 Performance and Scalability: 프레임워크는 추상화 계층으로 인해 성능 오버헤드가 발생할 수 있지만, 많은 프레임워크가 모듈식 아키텍처를 통해 확장성을 지원

- 프로젝트 요구 사항 Project Requirements: 프로젝트의 구체적인 요구 사항을 고려하세요. 예를 들어 실시간 애플리케이션을 구축하는 경우 WebSocket 통신을 지원하는 프레임워크가 유용할 수 있음.

- 신속한 개발 Rapid Development: 웹 프레임워크는 사전 빌드된 구성 요소를 제공하여 개발 프로세스의 속도를 높임.

- 에코시스템 및 커뮤니티 지원 Ecosystem and Community Support: 강력한 커뮤니티 지원과 라이브러리 및 도구 에코시스템을 갖춘 프레임워크를 선택할 필요. 문제 해결과 애플리케이션의 기능 확장에 도움이 될 수 있음.


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




