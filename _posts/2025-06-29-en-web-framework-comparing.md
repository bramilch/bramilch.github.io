---
layout: post
title: Types of web frameworks, comparing and choosing
author: bramilch
date: 2025-06-29 18:00:00 +0900
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

> 2024/05/21: Drafted 
> 2024/05/23: Added web frameworks table for each language 
> 2024/05/24: Added Spring, Django, Flask comparison 
> 2024/05/26: Added web framework selection criteria, pros and cons of specific web frameworks, improved 
> 2024/05/27: Added Spring vs. Spring Boot comparison 
> 2024/05/28: Corrected Spring vs. Spring Boot sentences, improved 
> 2024/05/29: Added Spring vs. Spring Boot features

 <br>
 
This content may contain errors.  
I am constantly adding, modifying, and supplementing the content.

<br>

**Table of Contents**
- [Preface](#preface)
- [Spring, Django, and Flask comparison](#spring-django-and-flask-comparison)
- [The problem with choosing a web framework](#the-problem-with-choosing-a-web-framework)
- [Front-End Web Frameworks](#front-end-web-frameworks)
- [Back-End Web Frameworks](#back-end-web-frameworks)
- [Full-Stack Web Frameworks](#full-stack-web-frameworks)
- [Comparing and choosing between Spring and Spring Boot](#comparing-and-choosing-between-spring-and-spring-boot)
	- [Spring Framework](#spring-framework)
	- [Spring Boot Framework](#spring-boot-framework)
- [Pros and cons of specific web development frameworks](#pros-and-cons-of-specific-web-development-frameworks)
	- [1. Django (Python)](#1-django-python)
	- [2. Flask (Python)](#2-flask-python)
	- [3. Spring (Java)](#3-spring-java)
	- [4. Express.js (JavaScript)](#4-expressjs-javascript)
	- [5. Ruby on Rails (Ruby)](#5-ruby-on-rails-ruby)
	- [6. Laravel (PHP)](#6-laravel-php)
	- [7. ASP.NET Core (C#)](#7-aspnet-core-c)
	- [8. Vue.js/Nuxt.js (JavaScript)](#8-vuejsnuxtjs-javascript)
	- [9. React.js/Next.js (JavaScript)](#9-reactjsnextjs-javascript)
	- [10. Angular (JavaScript/TypeScript)](#10-angular-javascripttypescript)
- [References](#references)


<br>

## Preface

<br>

- When you want to do web development, the time, personal and team effort, and cost is too great to develop everything yourself from zero code.

- To be more precise, there are web development frameworks (WF) and web application frameworks (WAF) for web development, including front-end web frameworks Front-End Web Frameworks, back-end web frameworks Back-End Web Frameworks, and full-stack web frameworks Full-Stack Web Frameworks.

- Many people have already created web frameworks as semi-finished products for web development ~~free, open source, thankfully!~~ that you can choose, modify, and mix and match to suit your project.

- However, web frameworks can be categorized into front-end, back-end, and full-stack, and there is a high probability that no single framework will cover all the features you need, so you need to consider their characteristics, pros and cons, and comparison before choosing and combining them.

- Also, each web framework has its own architecture, which requires time and effort to learn, so it is important to make a strategic choice.

- When I wanted to implement the service, the most important question I faced in terms of web development framework was whether to choose Spring, which is the standard framework for e-government in Korea and the most widely used Java-based framework, or Django and Flask, which are Python-based frameworks.

- Front-end, back-end, and full-stack web frameworks are essential components of web development, each of which plays a unique role and can determine the overall functionality and appearance of a web application. Understanding the differences and similarities between these ***frameworks is crucial to making an informed decision about which technology to use for a particular project.***

- To start, we'll look at web development frameworks based on Java and Python.

<br>

## Spring, Django, and Flask comparison

<br>

**Recap**.

- Spring Spring: Best for complex, enterprise-class applications that require high performance and scalability

- Django: Robust, full-featured framework best suited for rapid development

- Flask: Best for small to medium-sized applications that require flexibility and simplicity

<br>

<details><summary> On the web, Robust means </summary><div markdown="1">

<br>  

robust
_adjective_
1. strong and healthy; vigorous.
2. (of wine or food) strong and rich in flavor or smell.
from Google Dictionary
	
> "Robustness, as defined by WCAG, refers specifically to **web content that is compatible with a variety of “user agents”: browsers, assistive technologies, and other means of accessing web content**." by [WCAG 2.1 Principles Explained: Robustness](https://www.boia.org/blog/wcag-2.1-principles-explained-robustness#:~:text=Robustness%2C%20as%20defined%20by%20WCAG,means%20of%20accessing%20web%20content.)

> "Ensure your site looks and functions seamlessly on various screen sizes."

> "Robust: Web content should be made robust so that it is accessible with future technologies." 
> - Grammatical conformance (avoiding markup errors): Elements in the markup language should be free of errors in opening and closing, nested relationships, and attribute declarations.
> - Web application accessibility| (web application accessibility compliance): The web application embedded in the content must be accessible.
> by [문화체육관광부 국립장애인도서관 (웹 및 모바일) 접근성 Ministry of Culture, Sports and Tourism National Library for the Disabled (web and mobile) Accessibility](https://www.nld.go.kr/ableFront/new_standard_guide/accessibility.jsp)

</div></details>


<br>
<center><span style="font-size:1.2em;">Spring vs. Django vs. Flask</span></center>

<br>

|Features/Criteria|**Spring (Java)**|**Django (Python)**|**Flask (Python)**|
|---|---|---|---|
|**Languages**| Java |Python| Python|
|**Architecture**|Full-featured framework, MVC |Full-featured framework, MVT |Micro framework, WSGI|
|**Performance**|High performance and scalability|Excellent performance, but can be slower than Spring for large apps |Lightweight, can achieve high performance with proper optimization|
|**Ease of use**|Steep learning curve, Extensive configurations |Easy to use with "batteries-included" philosophy |Very easy to use, minimalist design|
|Flexibility*** Very flexible, extensive customization |Moderately flexible, conventions for configurations |Extremely flexible, minimal restrictions|
|Community Support*** Large, mature community |Large, active community |Large, active community |Large, active community|
|Libraries and Plugins*** Extensive ecosystem, lots of plugin support |Extensive built-in modules and third-party packages Many extensions available|
|Security*** High, Many built-in security features| High, many built-in security features available| Depends on extensions|
|**Development speed**|Slow due to complexity and configuration |Fast development with built-in features |Fastest due to simplicity|
|**Suitable projects**|Suitable for large enterprise-class applications |Fast development of robust web applications |Lightweight applications, microservices|
|**Limitations**|May be overkill for small projects|Can be monolithic and less flexible than Flask|Limited out-of-the-box features and relies on extensions|
|**Advantages**|High performance|Fast development|Simple and lightweight|
|Extensible|Easy to use|Flexible|
||Mature and stable|Great community and documentation|Great for microservices and small apps|
|Cons|Steep learning curve|May be slow for large apps|Not suitable for large monolithic apps|
|More complex setup|Less flexible than Flask|Fewer out-of-the-box features|

<br>

## The problem with choosing a web framework

<br>

- The choice between front-end, back-end, and full-stack frameworks depends on the ***specific requirements of the project (related to skills required, scalability)***, the expertise of the team (development capabilities, limited resources and time available, etc.), and the long-term goals of the application (also related to scalability).

**Project Requirements Project Requirements**
- Essential to determine the specific requirements, size, and complexity of the project. For example, if you are building a real-time application, a framework that supports WebSocket communication may be useful.   It's also essential to consider the specific features you need (e.g., real-time updates, handling large amounts of data)


**Development Speed vs. Control** Development Speed vs. Control
- If you need to get your product to market quickly, frameworks like Django or Rails with built-in features can save you time.
- If you need more control over your components, a micro-framework like Flask or Express.js may be a better fit.


**Learning curve Learning curve**
- Each framework has its own set of conventions and practices, which requires time to learn.

**Performance and Scalability Performance and Scalability**
- Frameworks can introduce performance overhead due to layers of abstraction, but many frameworks support scalability through modular architecture
- Performance Needs High-performance and scalable applications may benefit from frameworks like Spring or ASP.NET Core, while rapid development and flexibility may be better suited to Django or Flask.


**Rapid Development Rapid Development**
- Web frameworks provide pre-built components to speed up the development process.

**Ecosystem and community support Ecosystem and community support**
- Choose a framework with strong community support and an ecosystem of libraries and tools, which can help with troubleshooting and extending the functionality of your application.


## Front-End Web Frameworks

<br>

- Focuses on the user interface and user experience of a web application, organizing what users see and interact with in their browser.

- Technology: HTML, CSS, and JavaScript are the foundational technologies for front-end development. Popular frameworks that extend these skills and provide a more efficient and organized way to build UI user interfaces include React, Angular, and Vue.js.

- Frameworks and libraries: Bootstrap and Foundation Bootstrap and Foundation are widely used to structure and style web pages. React, Angular, and Vue.js are JavaScript frameworks/libraries that allow developers to create dynamic and responsive user interfaces.

- Ease of learning: Front-end development is generally easier to learn initially because it deals primarily with visual elements and user interaction without the complexity of server-side programming.

<br>

## Back-End Web Frameworks

<br>

- Concerned with the server-side logic of a web application. It handles data processing, business logic, and interaction with the database.

- Technology: Common backend languages include PHP, Ruby, Python, and Node.js. Frameworks like Ruby on Rails, Laravel, and Django provide structure and tools for building applications.

- Frameworks and libraries: Express.js is a minimalist Node.js framework that is widely used to build web applications and APIs. Other notable backend frameworks include ASP.NET Core for .NET applications and Spring Boot for Java applications.

- Complexity and control: Backend development is more complex and provides more control over server and database management, requiring a deep understanding of server-side programming and database management systems.

<br>

## Full-Stack Web Frameworks

<br>

- Includes both front-end and back-end development, allowing developers to work on all aspects of the web application.

- Technologies: Full-stack frameworks often combine technologies from both front-end and back-end development, for example, the MEAN/MERN stack (MongoDB, Express.js, Angular/React, Node.js) and the LAMP/LNMP stack (Linux, Apache/Nginx, MySQL/PostgreSQL, PHP/Python/Perl).

- Frameworks and libraries: Full-stack frameworks like MEAN/MERN provide a unified development environment, allowing developers to work seamlessly across the entire application stack using JavaScript.

- Versatility and efficiency: Full-stack development is highly regarded for its ability to streamline the development process and increase efficiency. It allows developers to understand and work with both the presentation layer and the underlying logic, giving them a holistic view of the application.

<br>

## Comparing and choosing between Spring and Spring Boot

<br>

**Choose based on your project's requirements, existing infrastructure, and development goals**.

- For new projects: If you are starting a new project and want to get up and running quickly with minimal configuration, Spring Boot is a good choice. It is especially suitable for microservices, RESTful APIs, and cloud-native applications.

- For existing projects: If you're maintaining or extending a legacy application that already uses the Spring framework, you may want to stick with the traditional Spring approach, especially if your application requires extensive customization and configuration.

- For learning: If you're new to the Spring ecosystem, starting with Spring Boot can help you grasp the basics before diving into the more complex Spring framework.

<br>

<center><span style="font-size:1.2em;">Spring vs Spring Boot</span></center>

|Features|Spring Framework|Spring Boot|
|-------------|-----------------|---|---------------|
|Purpose| Comprehensive framework for enterprise applications|Rapid applications with Spring|
|Development|High complexity, extensive configuration required|Low, automatic configuration and reasonable defaults|
|Configuration| XML, Java annotations, Java configuration|Configuration via rules, minimal setup|
|Embedded servers|Not included, external setup required|Embedded servers included (Tomcat, Jetty, Undertow)|
|Starter POM |Not included|Available, simplifies dependency management|
|Application setup|Manual setup required|Quick setup using the spring-boot-starter dependency|
|Microservices support|Configurable but complex|Provides built-in support for Spring Cloud|
|Production-ready features|Additional setup required|Built-in metrics, health checks, and monitoring|
|Learning curve|Steep due to extensive functionality|Gentle due to simplified setup and rules|
|Deployment|Existing WAR deployment|Executable JAR, easy to deploy

<br>

### Spring Framework

- The Spring framework is a comprehensive framework for enterprise Java development. It offers a wide range of features and is known for its ability to support large-scale application development.

**Key Features**.

- Dependency Injection (DI): The core of Spring, managing dependencies to enable loose coupling between components and facilitate testing and maintenance.

- Aspect-Oriented Programming (AOP)***: Allows cross-cutting issues such as logging and transaction management to be separated from business logic.

- Data access: Provides templates for integration with JDBC, ORM tools, and NoSQL databases to simplify data access.

- Transaction management: Provides a consistent programming model for managing transactions

- Web MVC***: A robust framework for building web applications with Model-View-Controller Architecture

- Security: Comprehensive security services for Java applications including authentication and authorization

<br>

**Features**

<br>

- Flexibility: Spring framework is highly flexible, allowing developers to create highly customized applications. Supports a variety of configurations, including XML, annotations, and Java-based configurations.

- Learning curve: Steep learning curve due to its comprehensive nature. Developers need to understand the various components and how they interact.

- Manual configuration: Requires significant configuration, which can be tedious and error-prone, especially for beginners.

- Ideal for large applications: Ideal for large, complex applications that require fine-grained control over configuration and behavior.

<br>

### Spring Boot Framework

- Spring Boot is built on top of the Spring framework. It is designed to simplify the setup and development of new Spring applications, making Spring more accessible and faster to develop with.

<br>

**Key features**

- Convention over Configuration: Provide defaults and configurations to minimize boilerplate code.

-------

> **What is boilerplate code**
> boilerplate code in computer programming boilerplate code or boilerplate boilerplate means ***a section of code that is repeated in many places with little or no variation***.
> boilerplate code boilerplate code etymology: iron rolled into large, flat plates for use in making steam boilers in the 1800s → ***"a unit of writing that can be used over and over again without change"***.
> Metaphorically became known as “boilerplate” when metal printing plates (letterpress metal) were distributed to small local newspapers for prepared text, such as advertisements or newspaper columns.

-------

- Embedded Servers: Comes with an embedded Tomcat, Jetty, or Undertow server to run web applications without the need for an external server.

- Starter POMs (Project Object Models): Simplifies dependency management by providing starter POMs that contain common dependencies for different types of applications (a house of dependency descriptors that you can conveniently include in your application)

- Production-Ready Features: Features like metrics, health checks, and externalized configuration are included by default

- Auto-Configuration: Automatically configures Spring applications based on dependencies that exist in the classpath
- 
<br>

**Features**

- Ease of use: Simplifies the development process by reducing the need for extensive configuration. Use rules and sensible defaults to get projects up and running quickly.

- Embedded server: Allows developers to package their application as a standalone JAR with an embedded server, simplifying deployment and reducing the need for external servers.

- Starter Dependencies: Provides a set of starter POMs that bundle common dependencies for different types of applications, making dependency management easier.

- Auto-Configuration Auto-Configuration: Automatically configures applications based on included dependencies to reduce boilerplate code and configuration.

- Microservices and cloud Microservices and cloud: Ideal for building microservices. Cloud-native applications Seamlessly integrates with Spring Cloud to build cloud-native applications.

- Ideal for developing microservices, RESTful APIs, and rapid prototyping: Quick setup and ease of use make it ideal for developing microservices, RESTful APIs, and rapid prototyping.

<br>

## Pros and cons of specific web development frameworks

<br>

<center><span style="font-size:1.2em;">Organizing web frameworks by Programming language</span></center>

<br>

|Main Languages Used|Framework Name|Description|
|---|---|---|
|**JavaScript**|React|A JavaScript React library for building user interfaces, especially single-page applications|
||Angular|A full-fledged framework for building web applications|
||Vue.js|A progressive framework for building user interfaces|
||Express.js|A Node. js web application framework|
|**Python**|Django|A Python web full-stack framework that encourages rapid development and clean, practical design|
||Flask|A Flask micro web framework written in Python|
|**PHP**|Laravel|A PHP framework that follows the Laravel MVC architecture pattern|
||Symfony|The Symfony PHP framework for web applications and services|
|**Java**|Spring Boot|Java Spring Boot Java-based framework for building standalone, production-grade Spring-based applications|
||Struts|Open source framework for building enterprise-grade Java web applications|
|**Ruby**|Ruby on Rails|Ruby on Rails Ruby framework that emphasizes rules over configuration|
||Sinatra|Sinatra DSL for quickly building web applications with Ruby|
|**. NET**|ASP.NET Core|Cross-platform .NET ASP.NET Core, a high-performance open source framework for building cloud-based, Internet-connected applications|
|**Go**|Gin|Go Gin HTTP web framework written in Golang|
|**Node.js**|Koa|Node.js Koa An expressive, powerful, and flexible framework for building web applications and APIs|
|**Rust**|Rocket|The Rust Rocket web framework for Rust that makes it easy to write fast and secure web applications|
|**Swift**|Vapor|The Swift web framework for building Swift Vapor web applications|
|**TypeScript**|NestJS|The TypeScript NestJS framework for building efficient and scalable Node. JS framework for building efficient and scalable Node.js server-side applications|
|**C#**|ASP.NET MVC|C# ASP. NET MVC model-view-controller framework for building web applications|
|**Scala**|Play|Scala Play high-speed web framework for Java and Scala|
|**Elixir**|Phoenix|Elixir Phoenix web framework built for building high-performance web applications|
|**Kotlin**|Ktor|Kotlin Ktor framework for building asynchronous servers and clients on connected machines using Kotlin|
|**Julia**|Genie. jl|Julia package for building web applications|
|**R**|Shiny|The R Shiny R package for building interactive web applications|

<br>

---------

> 1. **Django (Python)**
2. **Flask (Python)**
3. **Spring (Java)**
4. **Express.js (JavaScript)**
5. **Ruby on Rails (Ruby)**
6. **Laravel (PHP)**
7. **ASP.NET Core (C#)**
8. **Vue.js/Nuxt.js (JavaScript)**
9. **React.js/Next.js (JavaScript)**
> 10. **Angular (JavaScript/TypeScript)**

---------

### 1. Django (Python)

**Features**
- Full-featured, high-level Python framework that follows the Model-View-Template (MVT) architecture pattern

**Advantages**
- Built-in features allow for rapid development
- Strong community and extensive documentation
- Excellent security features
- Scalability for large applications

**Cons**
- Can be monolithic and inflexible compared to micro frameworks.
- May be overkill for small projects.

**A word of caution**
- Must carefully choose the size of the project to avoid unnecessary complexity.

### 2. Flask (Python)

**Features**
- A lightweight micro-framework for Python that provides essential features and increases flexibility

**Advantages**
- Very flexible and easy to use.
- Minimalism allows for customizable implementation
- Great for small to medium-sized applications and microservices

**Cons**
- Lacks built-in features and requires extensions for additional functionality
- Not suitable for large, complex applications and does not require customization.

**A word of caution**
- Dependencies must be carefully managed and necessary security features added.

### 3. Spring (Java)

**Features**
- A comprehensive framework for building enterprise-class applications in Java, following the Model-View-Controller (MVC) pattern.

**Advantages**
- High performance and scalability
- Strong security features
- Extensive ecosystem with tons of modules and extensions

**Cons**
- Steep learning curve
- Complex to set up and configure

**A word of caution**
- Complexity can be overwhelming, so consider if your team is proficient in Java and familiar with Spring

### 4. Express.js (JavaScript)

**Features**
- Minimalist web framework that's flexible enough to be used without being judgmental

**Advantages**
- Lightweight and fast
- Extremely flexible with a vast ecosystem (npm)
- Excellent for real-time applications

**Cons**
- Minimalist nature requires adding features manually
- Can lead to inconsistent code structure.

**A word of caution**
- Maintain consistent coding practices and structure across the team

### 5. Ruby on Rails (Ruby)

**Features**
- A full-stack framework for Ruby that follows the MVC pattern and emphasizes rules over configuration.

**Advantages**
- Rapid development with a rules-based approach
- Large community and good documentation
- Large set of built-in tools and libraries

**Cons**
- Performance can be poor for very heavily loaded applications.
- Less flexible due to rules.

**A word of caution**
- Evaluate your application's performance requirements to ensure Rails can handle the load

### 6. Laravel (PHP)

**Features**
- Full-featured PHP framework that follows the MVC pattern

**Advantages**
- Developer friendly with clean syntax
- Extensive built-in features and packages
- Strong community and great documentation

**Cons**
- Performance can be an issue for very large applications.
- PHP itself has fallen out of favor in some developer communities.

**What to watch out for**
- Monitor performance and optimize queries for scalability

### 7. ASP.NET Core (C#)

**Features**
- Cross-platform, high-performance framework for building modern cloud-based web applications

**Advantages**
- High performance and scalability
- Strong support for security and authentication
- Ideal for enterprise-class applications

**Cons**
- Requires knowledge of C# and the .NET ecosystem
- Can be complex to set up and configure


**Cautions**
- Make sure your team is familiar with the Microsoft stack and .NET Core environment

### 8. Vue.js/Nuxt.js (JavaScript)

**Features**
- Nuxt.js, a progressive JavaScript framework for building user interfaces, extends Vue.js with server-side rendering

**Benefits**
- Responsive and component-based architecture
- Easy to learn and easy to integrate.
- Great for single-page applications (SPAs)

**Cons**
- Limited ecosystem compared to React
- Can be overkill for simple applications.

**What to watch out for**
- Make sure the complexity of Nuxt.js matches your project requirements

### 9. React.js/Next.js (JavaScript)

**Features**
- Library (Next.js) for building user interfaces (React) with framework for server-side rendering and static site creation

**Advantages**
- High performance and flexibility
- Large community and extensive ecosystem
- Great for complex SPAs and dynamic web applications

**Cons**
- Steep learning curve for beginners
- Can result in boilerplate code without proper structuring

**What to watch out for**
- Properly manage and optimally structure state to avoid complexity

### 10. Angular (JavaScript/TypeScript)

**Features**
- Full-fledged framework for building dynamic web applications developed by Google

**Advantages**
- Comprehensive solution with everything you need for front-end development
- Robust support for building large-scale applications
- TypeScript support adds type safety

**Cons**
- Steep learning curve
- May be overkill for small projects

**What to watch out for**
- Consider the size and complexity of your project



## References

[문화체육관광부] 국립장애인도서관 (웹 및 모바일) 접근성  National Library of Disability (web and mobile) accessibility
<https://www.nld.go.kr/ableFront/new_standard_guide/accessibility.jsp>

WCAG 2.1 Principles Explained: Robustness  
<https://www.boia.org/blog/wcag-2.1-principles-explained-robustness#:~:text=Robustness%2C%20as%20defined%20by%20WCAG,means%20of%20accessing%20web%20content>

[Online Etymology Dictionary] boilerplate (n.)  
<https://www.etymonline.com/word/boilerplate>