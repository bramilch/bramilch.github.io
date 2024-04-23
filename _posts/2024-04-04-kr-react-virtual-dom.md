---
layout: post
title: "리액트 React Virtual DOM 개념과 동작방식 feat. 원티드 프리온보딩 챌린지 4월"
author: bramilch
date: 2024-04-04 18:00:00 +0900
categories: [Web Development, Frontend]
tags: [Web Development, Frontend]
pin: false
math: true
toc: true
comments: false
mermaid:
  false
  # alt: Responsive rendering of Chirpy theme on multiple devices.
---

<br>

> 2024/04/02: 초안 작성  
> 2024/04/21: Internal Link 오류 수정 완료

※ 이 글은 작성자에게 블로그 글 작성 소재가 되어준 원티드 교육 프로그램과 강사님들에 대한 고마운 마음으로 작성하였고, 좋은 교육 프로그램을 소개하고자 광고 받지 않고 작성하였습니다. 원티드 관계자 분들과 강사님들, 참고한 블로그의 작성자 분들께 감사드립니다.

<br>

**목차**

- [머리말](#머리말)
- [DOM과 Virtual DOM](#dom과-virtual-dom)
  - [자바스크립트 자료구조 JavaScript Data Type](#자바스크립트-자료구조-javascript-data-type)
  - [자료구조 객체(Object)와 DOM](#자료구조-객체object와-dom)
- [Virtual DOM 개념과 동작 방식](#virtual-dom-개념과-동작-방식)
- [참고자료](#참고자료)

<br>

## 머리말

- 원티드 프리온보딩 챌린지 4월 프론트엔드 FE의 사전과제를 작성하며 정리한 내용을 작성함.
  <br>
  <details><summary> 원티드 프리온보딩 챌린지란 </summary><div markdown="1">
    <br> 
    - 총 5가지 프로그램이 진행됨.

        1. 포트폴리오에 Docker로 배포 경험 더하기
        2. 실무에서 바로 적용 가능한 리액트 핵심 기술
        3. UX/UI 실무 프로세스부터 팁&노하우까지
        4. 핵심 성과중심의 PO 포트폴리오 만들기
        5. 취업 특강 with SQL, Tableau

  - 매월 모집기간 동안 참가자를 모집함.

  - 프로그램 목적은 '면접에서 어필 가능한 핵심 기술/주제만 집중 학습'

  - 내가 추측한 프로그램 주요 기획 의도는 원티드 교육사업 내에서 주 이용자인 구직자와 커리어 관련 교육 프리랜서 유입과 풀 형성, 기업의 원티드 프리랜서 매칭/프로젝트 아웃소싱 플랫폼으로의 유입 연계, 데이터 확보와 포트폴리오인 것 같음.

  - 사전미션은 필수로 수행해야 하는 것은 아님. 강사님에 따라 교육 내용과 관련되어 수행하는 경우, 간단한 설문인 경우도 있음.

  - '역량 향상 세션'은 온라인으로 실시간 3시간씩 주 2회로 2주간 진행

  - 라이브로 참여하지 못 하거나 추가 복습을 위해 총 4회차 영상을 3개월간 1만 원으로 다시 볼 수 있음.

  - 세션 2주 진행 후 '취업 챌린지'란 이름으로 주차 별 챌린저 지원 현황 공유, 단계 별 취업 레시피, 채용 큐레이션 페이지가 제공됨.

  - 이 외에, 챌린지를 수료하고 원티드를 통해 취업에 성공하면 최대 200만 원 합격 축하금 지급, 맞춤 도서 추천하고, 적극 구직자 5명 선정하여 길벗 IT 추천 도서 전자책 증정이 있음.

  </div>
  </details><br>

  <details><summary> 프론트엔드 챌린지 4월 내용 </summary><div markdown="1"><br>

  실무에서 바로 적용 가능한 리액트 핵심 기술 | 프리온보딩 FE 챌린지 4월
  <https://www.wanted.co.kr/events/pre_challenge_fe_20>

  아래의 내용은 위 링크의 내용을 그대로 참고하였습니다.

  - 교육 목표

    1. 프로젝트 초기, 기획안과 UI를 기반으로 체계적인 컴포넌트 분리와 파일 구조 작성 전략 학습
    2. 필수적이고 즉시 활용 가능한 리액트 개념을 빠르고 간단하게 학습
    3. 리액트스러운 효율적이고 표준적인 코드 작성법 학습
    4. 면접에서 리액트의 표준 코드 작성법과 프론트엔드 시각으로 기획안 및 UI/UX를 체계적으로 구조화하는 지식에 대해 답할 수 있도록 학습<br>

    <details><summary> 커리큘럼 </summary><div markdown="1"><br>
      
      - Week 1-1
        리액트의 핵심 원리를 소개합니다.
        - 웹 개발 기초 및 리액트 기초 이해
          - 웹 개발의 기본 요소인 HTML, CSS, JavaScript 학습
          - JSX 문법 소개
          - 리액트의 가상 DOM
          - State의 개념과 단방향 데이터 흐름
          - (아하모먼트) 비전공자(신입)이기에 내새울 수 있던 서류/면접 합격 전략

    - Week 1-2
      리액트에서 필수적으로 사용하는 Hooks과 SPA을 배웁니다.

      - Hooks과 SPA
        - useState를 이용한 상태 변경
        - useEffect를 활용한 컴포넌트 생명주기 관리
        - React Router를 활용한 페이지 네비게이션 구현
        - 페이지 간 데이터 전달 및 라우팅 파라미터 활용
        - (아하모먼트) 프론트엔드에게 개발 실력만큼 중요한건?

    - Week 2-1
      서버와의 데이터 통신을 통한 동적 화면 구현합니다.

      - RestFul API
        - RestFul API의 개념
        - CRUD
        - Aioxs를 이용하여 데이터 요청하기
        - 동적으로 데이터 변경하기
        - (아하모먼트) 신입과 사수의 입장에서 겪은 나의 고민

    - Week 2-2
    기능 구현 말고 또 신경써야할 A-Z - UI/UX과 협업 - 반응형 웹 디자인 및 레이아웃 최적화 - UI/UX의 중요성 - SEO를 고려하기 - 효과적인 커뮤니케이션 및 협업 - (아하모먼트) 이직과 성장을 고민하는 순간
    </div>
    </details>

  </div>
  </details><br>

- 우연히 발견한 원티드 프리온보딩 챌린지 4월 시리즈 중 포트폴리오에 Docker로 배포 경험 더하기가 현재 준비하고 있는 웹 서비스, 데이터 분석 포트폴리오에 도움이 될까 유심히 보다가 5개를 모두 신청함.

- 무료인 점과 라이브로 참가하지 못 하는 역량 향상 세션 모두를 3개월간 1만 원으로 다시 볼 수 있어 시간을 효율적으로 활용할 수 있는 점이 선택한 가장 큰 이유 2가지

- 가장 필요했던 것은 백엔드, 프론트엔드, 디자인 부분

- 데이터분석과 웹 서비스 포트폴리오 수행 중 클라우드, Docker, CI/CD, React, UX/UI 기초 지식과 툴 사용법, 실무 Tips에 대한 빠른 학습이 필요했음.

- 직무 경력자를 통해 경험해보지 못 한 직무의 실무에 대한 감을 익히고자 함.

- 커리큘럼의 교육 목표와 내용이 너무 과장되지 않고 면접과 기초 지식 학습에 도움이 될 것 같았음.

<br>

<details><summary> 원티드 회사 사업 내용과 프리온보딩 챌린지 사업 리서치 </summary>
<div markdown="1"><br>

- 원티드는 B2C 구인/구직/이직 매칭 사업, B2B HR 솔루션 사업, 커리어/HR 연관 사업(교육/콘텐츠/이벤트/코칭/네트워킹)이 주이고, 기업 리뷰 플랫폼 사업과 프리랜서 매칭/아웃소싱 플랫폼 사업으로 확장하려는 것으로 보임.

  - 잡플래닛과 같은 크레딧잡을 2018년도에 인수하여 [원티드 인사이트](https://www.wanted.co.kr/events/pre_challenge_fe_20/)를 운영하고 있음. ~~크레딧잡 시절에 꽤 이용했으나 난 잘 사용하지 않음.~~

- HR과 관련한 다양한 솔루션을 제공하고 있는데, 채용 솔루션('원티드 채용 솔루션'), HR 업무 솔루션(원티드 스페이스), 프리랜서 매칭 솔루션(원티드 긱스), 기업 리뷰 플랫폼인 원티드 인사이트와 연계하여 연봉, 인원, 매출, 전·현직자 리뷰 등을 관리할 수 있게 해주는 솔루션(원티드 인사이트)가 있음.

- 최근 구인/구직/커리어 교육 기업들의 수강생과 수료생, 교육 프로그램 관리를 위한 B2B/B2G 솔루션 원티드 취업지원시스템을 런칭한 것으로 보임. 현재는 주로 취준생을 타겟팅한 구직 직무 교육기업/기관들에게 큰 돈줄이 되고 있는 고용노동부의 '국민내일배움카드' 사업에서의 교육 수강생들의 구직 활동, 취업 성과까지 관리할 수 있게 하여 구직 직무 교육기업/기관들의 연계 위한 솔루션으로 보이나 현직, 이직러들을 타겟팅한 커리어/직무 교육기업 패스트캠퍼스와 같은 비즈니스 모델도 염두에 두는 것으로 보임.

</div>
</details><br>

<details><summary> 온보딩(Onboarding)과 프리온보딩(Pre-Onboarding)의 차이 </summary>
<div markdown="1"><br>
  
- 인사조직관리 분야에서 온보딩(Onboarding)은 조직사회화(Organizational Socialization)라고도 함.

- 온보딩(Onboarding)은 근무시작일부터 조직의 일원으로서 필요한 지식, 스킬, 행동 등의 교육 과정을 뜻함.

- 프리온보딩(Pre-Onboarding)은 입사 결정 이후 근무시작일 전까지 온보딩을 준비하는 기간을 말함. ~~검색 결과가 빈약한 것으로 보아 프리온보딩 프로세스 문화는 외국에서도 발달되어 있어보이지 않음.~~

</div>
</details><br>

## DOM과 Virtual DOM

### 자바스크립트 자료구조 JavaScript Data Type

- 자바스크립트의 Data Type엔 총 8가지가 있음.

  > Primitive Type 7가지

  - Number, BigInt, String, Null, Undefined, Boolean, Symbol

  > 객체형(Object Type, Reference Type) 1가지

  - Primitive Type을 제외한 함수, 배열, 객체(Object)

- 객체, 배열, 함수는 Primitive Type과 달리 복합적인 자료를 표현할 수 있고, 그 중 객체(Object)는 중괄호 { }를 이용해 Key와 Value로 구성된 Property 집합으로 만들 수 있음.

<br>

### 자료구조 객체(Object)와 DOM

- 객체(Object)는 다음 3가지로 나눌 수 있음.

  > 1. 내장 객체(Built-in Objects)
  > 2. 브라우저 내장 객체(Native Object)
  > 3. 사용자 정의 객체(Host Object)

<br>

- 브라우저 내장 객체(Native Object)에는 브라우저 객체 모델(BOM, Browser Object Model), 문서 객체 모델(DOM, Document Object Model)로 구성됨.

- 내장 객체(Built-in Objects)는 자바스크립트 엔진에 내장되어 있다는 의미로, 필요한 경우에 생성해서 사용할 수 있음.

- 브라우저 객체 모델(BOM, Browser Obejct Model)은 브라우저에서 계층 구조로 내장되어 제공하는 객체이고 브라우저에 관한 정보 제공, 모양 제어하는 정보가 포함되어 있음.

<br>

- BOM은 웹 브라우저가 열릴 때마다 생성되는 객체들이 있음.

  - 최상위 관리 객체인 Window 객체
  - Document 객체(HTML 문서 정보 포함)
  - Location 객체(현재 표시된 페이지에 대한 URL 정보 포함)
  - History 객체(웹 브라우저에 저장된 방문 기록이 포함)
  - Navigator (웹 브라우저 정보가 포함된 객체)
  - Screen (웹 브라우저의 화면 정보가 포함된 객체) 등

<br>

- DOM(Document Object Model, 문서 객체 모델)은 프로그래밍 언어가 XML이나 HTML 문서에 접근하기 위한 구조, 표현(인터페이스)임.

  > W3C DOM, WHATWG DOM 표준을 대부분의 브라우저에서 사용하고, W3C DOM은 모든 문서 타입을 위한 Core DOM, HTML 문서를 위한 HTML DOM, XML 문서를 위한 XML DOM의 3가지가 있음.

- 브라우저는 HTML 페이지를 로드하면서 HTML 태그는 포함관계(부모자식 관계)에 따라 태그당 하나씩 태그 이름을 가진 HTML DOM 객체들로 만들고, HTML DOM 객체들의 포함관계로 만든 트리구조로 DOM 트리를 만듦.

- BOM의 Window 객체에 속하는 Document 객체는 DOM 트리 구조의 최상위 객체임. Document 객체는 DOM 객체가 아니라 BOM 객체임.

- 브라우저는 HTML문서 로드 전 Document 객체를 먼저 생성하고, Document 객체를 최상위 객체로 하는 DOM 객체들로 구성된 DOM 트리를 생성함. 웹 페이지에 존재하는 HTML 요소에 접근하고자 할 때는 반드시 Document 객체에 접근하여야 함.

<br>

## Virtual DOM 개념과 동작 방식

- DOM(Document Object Model)은 웹 페이지를 이루는 태그들을 자바스크립트가 이용할 수 있게끔 브라우저가 트리구조로 만든 객체 모델

- DOM은 HTML, XML 등 문서의 트리 구조로 표현되고, 스크립트가 문서의 내용, 구조, 스타일에 동적으로 접근하고 수정할 수 있도록 함.

- Virtual DOM은 렌더링을 최소화해서 속도를 향상시키고 버그, 브라우저 멈춤(Freezing)을 개선하기 위해 DOM을 직접 수정하는 대신 메모리에 해당하는 버전의 Vitual DOM을 생성한 후 비교해서 변경된 부분만 DOM을 업데이트하는 방법

- Virtual DOM 동작 방식

  1. 컴포넌트가 변화할 때 React는 DOM을 직접 수정하지 않고 Virtual DOM을 메모리에 생성

  2. React가 이전 Virtual DOM의 스냅샷과 현재 생성한 Virtual DOM을 비교, 차이점 확인

  3. 변경된 DOM 부분만 수정

<br>
<br>

## 참고자료

실무에서 바로 적용 가능한 리액트 핵심 기술 | 프리온보딩 FE 챌린지 4월
<https://www.wanted.co.kr/events/pre_challenge_fe_20>

Onboarding  
<https://en.wikipedia.org/wiki/Onboarding>

7 tips for successful pre-onboarding  
<https://www.linkedin.com/pulse/7-tips-successful-pre-onboarding-kronos-consulting-dubai/>

[JavaScript] 자바스크립트의 객체 모델 DOM, BOM  
<https://codingwanee.tistory.com/entry/JavaScript-%EB%B8%8C%EB%9D%BC%EC%9A%B0%EC%A0%80-%EA%B0%9D%EC%B2%B4-%EB%AA%A8%EB%8D%B8-BOM>

[Javascript] 객체 모델 BOM, DOM  
<https://welldoing-dogfoot.tistory.com/10>

[React] DOM이란? 가상 돔 (Virtual DOM )이 나오게 된 이유  
<https://dev-cini.tistory.com/10>

[React] Virtual DOM(가상돔)  
<https://jooy34.tistory.com/17>
