---
layout: post
title: "서블릿 Servlet 실행 시 톰캣 서버 오류 해결 feat. 삽질의 기록"
author: bramilch
date: 2024-04-23 18:00:00 +0900
categories: [Backend, Data Engineering]
tags: [Backend, Data Engineering]
pin: true
math: true
toc: true
comments: false
mermaid:
  false
  # alt: Responsive rendering of Chirpy theme on multiple devices.
---

<br>

> 2024/04/25: 초안 작성

※ 삽질은 피가 되고 뼈가 됨. 백엔드 시 맞닥뜨리는 문제 해결 능력을 키우는 과정이자 많이 배울 수 있지만 역시나 효율적인 삽질이 필요  
※ 성장의 보조 도구인 생성형 AI에서 무엇이 문제인지 단서가 없는 경우, 정의와 맥락을 설명하기조차 어려운 상황에선 어떻게 원하는 답을 얻어낼 수 있을 것인지 고민 필요

<br>

**목차**

- [해결 방법](#해결-방법)
- [문제 발단: 이클립스에서 Servlet 실행 시 맞닥뜨린 톰캣 서버 오류](#문제-발단-이클립스에서-servlet-실행-시-맞닥뜨린-톰캣-서버-오류)
- [생성형 AI가 알려주는 더 큰 삽질을 피하는 방법](#생성형-ai가-알려주는-더-큰-삽질을-피하는-방법)
- [문제 원인 파악: Java Annotation과 Web.xml에서의 url-pattern 값의 충돌](#문제-원인-파악-java-annotation과-webxml에서의-url-pattern-값의-충돌)
- [문제 해결: Java Annotation과 url-pattern 값 둘 중 하나만 선택](#문제-해결-java-annotation과-url-pattern-값-둘-중-하나만-선택)
- [깨달은 점](#깨달은-점)

<br>

## 해결 방법

**참고: Tomcat v10.1**

- Java Annnotation @WebServlet("/URI")과 Web.xml에서 <url-pattern>/URI</url-pattern>는 둘 중 하나만 선택해야 함. 충돌로 인해 서버가 아예 돌아가지 않음.
- 만약 Java Annotation을 썼을 경우엔 <url-pattern></url-pattern> 빈 공간으로 두어야 하고, <url-pattern>/URI</url-pattern>를 넣었을 경우엔 Java Annotation을 서블릿 본문에 넣지 말아야 함.

<br>

## 문제 발단: 이클립스에서 Servlet 실행 시 맞닥뜨린 톰캣 서버 오류

- Servlet을 생성하고, doGet, doPost 등 메서드 오버라이딩 하고 Run on Server 하니 갑자기 맞닥뜨린 톰캣 서버 오류
- 아예 서버가 Stopped 되고 돌아가지 않음.
- 치명적인 것은 정상적인 다른 Servlet을 실행해도 되지 않는다는 것.

![Problem Occured](.\assets\img\posts\2024-04-25-kr-today-learned\problem-occured-popup.png)  
'Starting Tomcat v10.1 Server at localhost' has encountered a problem.  
~~detail에서도 설명 안 해주는 센스!~~

- 콘솔에서의 오류 메세지에서도 어떤 component가 오류났는지 설명하지만 단서를 찾기 어려움.

```
Caused by: java.util.concurrent.ExecutionException: org.apache.catalina.LifecycleException: Failed to start component [StandardEngine[Catalina].StandardHost[localhost].StandardContext[/package name]]
~~~
~~~
Apr 00, 2024 00:00:00 AM org.apache.coyote.AbstractProtocol pause
INFO: Pausing ProtocolHandler ["http-nio-8080"]
Apr 00, 2024 00:00:00 AM org.apache.catalina.core.StandardService stopInternal
INFO: Stopping service [Catalina]
Apr 00, 2024 00:00:00 AM org.apache.coyote.AbstractProtocol destroy
INFO: Destroying ProtocolHandler ["http-nio-8080"]

```

- 서블릿에 문법 오류, import 안 된 것들이 있나 확인했으나 없음.
- Eclipse 재시작해도 소용없음.
- 잦은 서버 중단과 재시작으로 오류가 났는지 등 톰캣 서버 자체에 오류가 있을 가능성을 보고 Servers 탭에서 해당 모듈 서버만 삭제해보고 다시 Run해도 같은 오류 팝업 등장
- 톰캣 서버 Clean해도 같은 오류 팝업 등장
- 톰캣 Remove 해도 소용없음.
- 구글링을 통하니 아예 톰캣 삭제, Repo 삭제, 이클립스 톰캣 환경설정 삭제, 포트번호 바꾸기 방법도 있으나 아닌 것 같아 넘김.
- 그 중 Indian English를 구사하는 귀여운 유튜브 영상과 귀여운 혀 발음 속 Web.xml의 <url-pattern>/URI</url-pattern>에서 URI를 삭제하니 잘 작동되는 것을 발견
- 적용해보니 서버가 돌아가는 것을 확인. 그러나 콘솔 프린트가 목적인데 콘솔 프린트가 안 됨.
  ~~다른 분들도 이런 삽질들이 많겠지만 삽질 기록의 의미가 없다고 생각이 듦~~

## 생성형 AI가 알려주는 더 큰 삽질을 피하는 방법

- 생성형 AI에게 힌트를 얻고자 질문
- 도대체 오류 힌트가 없어 "When I run servlet in Eclipse, I get this error message "Server Tomcat v10.1 Server at localhost failed to start.". How to solve it?"라고 밖에 묻지 못 함.

- 생성형 AI의 답변

  > Eclipse에서 "Server Tomcat v10.1 Server at localhost failed to start"라는 오류 메시지는 구성 문제부터 버전 비호환성에 이르기까지 다양한 문제로 인해 발생할 수 있습니다. 이 문제를 해결하고 잠재적으로 해결할 수 있는 몇 가지 단계는 다음과 같습니다.

  > 1. Tomcat 버전 호환성 확인
  >    > 사용 중인 Tomcat 버전이 프로젝트 요구 사항과 호환되는지 확인하세요. Tomcat v10.1은 비교적 최신 버전이므로 모든 Java EE 기술 또는 이전 버전의 Java와 완전히 호환되지 않을 수 있습니다. 프로젝트가 이전 버전의 Tomcat용으로 설계된 경우 해당 버전을 대신 사용하는 것이 좋습니다.

  > 2. Tomcat 설치 확인
  >    > 올바른 설치: Eclipse에서 Tomcat이 올바르게 설치 및 구성되었는지 확인하십시오. Window > Show View > Servers로 이동하여 Tomcat이 나열되어 있는지 확인하세요. 그렇지 않은 경우 추가해야 할 수도 있습니다.
  >    > Tomcat 구성: 서버 보기에서 Tomcat을 마우스 오른쪽 버튼으로 클릭하고 열기를 선택합니다. 구성, 특히 Tomcat 설치 디렉터리와 HTTP/1.1 커넥터 포트가 올바른지 확인하세요.

  > 3. 포트 충돌 확인
  >    > 포트 충돌: Tomcat의 기본 포트는 8080입니다. 다른 응용 프로그램이 이 포트를 사용하고 있으면 Tomcat이 시작되지 않습니다. Eclipse의 Tomcat 구성에서 포트를 변경할 수 있습니다.
  >    > 방화벽 또는 바이러스 백신 소프트웨어: 때때로 방화벽이나 바이러스 백신 소프트웨어가 Tomcat 시작을 차단할 수 있습니다. 일시적으로 이를 비활성화하여 문제가 해결되는지 확인하십시오.
  > 4. Tomcat 로그 검토
  >    > 로그 파일: Tomcat 로그는 서버 시작 실패 이유에 대한 자세한 정보를 제공할 수 있습니다. Tomcat 설치의 로그 디렉토리에서 로그를 찾으십시오.
  >    > 오류 메시지: 문제에 대한 단서를 제공할 수 있으므로 로그의 특정 오류 메시지에 주의를 기울이십시오.

  > 5.  Eclipse 및 Tomcat 업데이트
  >     >     Eclipse 업데이트: Eclipse IDE가 최신인지 확인하세요. 오래된 IDE는 최신 버전의 Tomcat을 완전히 지원하지 않을 수 있습니다.
  >     >
  >     > Tomcat 업데이트: 이전 버전의 Tomcat을 사용하는 경우 프로젝트와 더 잘 호환되는 최신 버전으로 업데이트하는 것이 좋습니다.

  > 6. 프로젝트 정리 및 재구축
  >    > 프로젝트 정리: Eclipse에서 프로젝트를 마우스 오른쪽 버튼으로 클릭하고 정리를 선택합니다. 이렇게 하면 컴파일된 모든 파일이 제거되고 강제로 다시 빌드되므로 문제가 해결되는 경우도 있습니다.
  >    > 프로젝트 다시 빌드: 정리 후 프로젝트를 다시 빌드하여 모든 변경 사항이 적용되도록 합니다.

  > 7.  프로젝트 종속성 확인
  >     >     누락된 종속성: 필요한 모든 라이브러리와 종속성이 프로젝트에 올바르게 포함되어 있는지 확인하세요. 종속성이 없거나 잘못된 경우 Tomcat이 시작되지 않을 수 있습니다.

  > 8. 이클립스를 다시 시작하세요
  >    > 다시 시작: 때로는 Eclipse를 다시 시작하는 것만으로도 Tomcat 시작을 방해하는 일시적인 문제를 해결할 수 있습니다.

  > 이러한 단계를 시도한 후에도 문제가 지속되면 Tomcat 커뮤니티나 포럼에서 도움을 구하는 것이 좋습니다. Tomcat 로그의 자세한 정보를 제공하면 다른 사람들이 문제를 보다 효과적으로 진단하는 데 도움이 될 수 있습니다.

<br>

- 그래....다 맞는 말이긴 한데...문제가 커지는 것 같은 불길한 예감
- 이 중에서 톰캣 로그 확인이 가장 정확해 보여 톰캣 로그 확인했으나 로그도 제대로 남지 않음.
- **아예 오류가 나는 Sevlet을 삭제 + Web.xml 부분에서 해당 Sevlet 부분 삭제**
- **다시 Package에서 New를 통해 Servlet 생성하니 정상 작동**

- 문제의 원인을 정확히 알지 못한 채 문제 해결 후 넘어가게 됐으나...

<br>

## 문제 원인 파악: Java Annotation과 Web.xml에서의 url-pattern 값의 충돌

- 새로운 Servlet 생성 후 Run on Server하니 똑같은 오류 발생 ~~으악!!!~~
- 처음 Servlet을 만들어도 Java Annotation을 자동으로 만들어주지 않음.
- 아까 url-pattern의 값을 아예 없애면 서버가 돌아간 것이 떠오름.
- Java Annotation과 url-pattern의 값이 충돌이 나는 것 아닐까?
- 같이 적은 경우, 번갈아가며 해본 결과 Java Annotation과 url-pattern의 값이 충돌로 결론

<br>

## 문제 해결: Java Annotation과 url-pattern 값 둘 중 하나만 선택

- Java Annnotation @WebServlet("/URI")과 Web.xml에서 <url-pattern>/URI</url-pattern>는 둘 중 하나만 선택해야 함. 충돌로 인해 서버가 아예 돌아가지 않음.
- 만약 Java Annotation을 썼을 경우엔 <url-pattern></url-pattern> 빈 공간으로 두어야 하고, <url-pattern>/URI</url-pattern>를 넣었을 경우엔 Java Annotation을 서블릿 본문에 넣지 말아야 함.

<br>

## 깨달은 점

- 삽질의 과정에서 얻은 단서로 의심의 의심, 시험해본 결과 결론에 다다름.
- 아주 구체적인 Technical Issue에서 Trouble Shooting을 잘하려면 역시나 기초 지식과 요소들의 관계를 파악할 수 있어야 함. 작은 단서로부터 문제 해결은 시작됨.
