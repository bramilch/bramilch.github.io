---
layout: post
title: "자바스크립트 JavaScript 함수와 호이스팅 Hoisting"
author: bramilch
date: 2024-04-26 18:00:00 +0900
categories: [Frontend, Data Engineering]
tags: [Frontend, Data Engineering]
pin: true
math: true
toc: true
comments: false
mermaid:
  false
  # alt: Responsive rendering of Chirpy theme on multiple devices.
---

<br>

> 2024/04/26: 초안 작성

※ 내용에 오류가 있을 수 있습니다.

<br>

**목차**

- [자바스크립트 함수 특성, Call Stack, 기본 return 값, 키워드 arguments](#자바스크립트-함수-특성-call-stack-기본-return-값-키워드-arguments)
- [함수선언식, 함수표현식과 호이스팅 Hoisting](#함수선언식-함수표현식과-호이스팅-hoisting)

<br>

## 자바스크립트 함수 특성, Call Stack, 기본 return 값, 키워드 arguments

<br>

- 자바스크립트에서는 함수가 상당히 중요

- 함수를 연속적으로 호출하는 Call Stack 이해를 기반으로 프로그램 로직 구현, 디버깅, 성능 개선을 위한 분석이 상당히 중요함.

- 자바스크립트를 잘한다는 것은 자바스크립트 함수를 잘 다룬다는 것.

- 자바스크립트 함수는 아무 내용이 없어도 undefined를 return하게 되어 있음.
  - 다른 언어에서 함수가 아무 것도 반환하지 말라는 return 타입이 없다는 의미인 void와 같은 것이 없음.

<br>

```
function test(){};
console.log(test());
```

콘솔 결과값

```
undefined
```

<br>

- 함수 파라미터 변수명을 적지 않아도, 내용이 아무 것도 없어도 undefined를 반환하도록 되어있기 때문

- 변수명 따로 임시로 만들지도 않고 return으로 undefined 데이터타입의 primitive 변수를 반환하는 것 같음.

- 함수의 파라미터 개수와 argument 개수가 달라도 오류가 나지 않고, 함수 파라미터 순서와 개수만큼만 적용됨.

- 함수 파라미터로 전달되는 인자들은 변수 선언을 따로 하지 않아도
  함수가 실행되면 그 안에는 **_arguments_**라는 변수명으로 key-value의 object 지역변수가 자동으로 생성하여 하나씩 접근할 수 있음.

- 함수선언식에 arguments 변수를 생성해서 호출할 때 전달하는 arguments들을 object 객체로 다 받는 것으로 보임.

- arguments는 조심히 써야 됨.

<br>

> <span style="font-size:1.2em;">**_전달되는 argument 개수를 체크하는 등 필요하고 의도를 가진 경우에 써야하고, 함수의 인자 값이 바뀔 가능성 등 변경에 약하기 때문에 arguments를 함부로 수정해서도 안 됨._**</span>

<br>

## 함수선언식, 함수표현식과 호이스팅 Hoisting

<br>

- 자바스크립트에서 함수를 만드는 방식은 2가지가 있다. 1. 함수 선언문(바로 함수 객체 생성), 2. 함수 표현식(변수에 함수를 할당)

- 자바스크립트는 호이스팅 방식으로 코드들을 실행하는데, JS파서가 먼저 변수 선언한 것들을 모으고, 함수는 통째로 가져와(함수 표현식에선 함수를 할당한 변수만 가져옴) 맨 위로 끌고 와서 먼저 선언함.

- 함수 표현식의 변수만 선언하고 값을 할당하지 않아 undefined가 된 상태에서 함수 표현식의 함수를 호출하면 오류가 날 수 있음.

<br>

> <span style="font-size:1.2em;"> **_따라서 함수 표현식은 함수를 할당한 변수와 할당할 함수의 코드라인 순서가 중요함._**</span>
