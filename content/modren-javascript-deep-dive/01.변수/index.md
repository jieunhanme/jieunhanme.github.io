---
emoji: 🤿
title: 변수 Variable
date: '2022-12-07 22:30:00'
author: 한지은
tags: 블로그 JavaScript 모던자바스크립트DeepDive study
categories: JavaScript
---

## 변수란

> 값을 재사용 할 수 있도록 하나의 값이 저장된 메모리 주소를 `식별`하는 상징적인 이름을 뜻합니다

**변수명을 사용해 참조를 요청하면 자바스크립트 엔진은 변수명과 매핑된 메모리 주소를 통해 메모리 공간에 접근해 저장된 값을 반환합니다**  

값 할당(assingment)  
let result = 10 + 20;  
<sub>변수명(식별자)</sub><sub>변수 값</sub>  
console.log(result) 참조(reference)

> 식별자 indentifier
>> 식별자는 어떤 값을 구별해서 식별할 수 있는 **고유한 이름**으로 값이 아니라 `메모리 주소`를 기억하고 있다  
변수, 함수, 클래스 등 메모리 상에 존재하는 어떤 값을 식별할 수 있는 이름은 모두 식별자라고 부른다


## 변수 선언

변수를 사용하려면 <abbr title="var 키워드는 사용을 지양하는 추세입니다">var</abbr> let, const 키워드를 사용해 반드시 선언을 해야합니다

<div class="codebox-title">변수 선언문</div>

```javascript
let socre;
```

자바스크립트 엔진은 변수 선언을 다음과 같은 2단계에 거쳐 수행합니다
1. 선언 단계 : 변수 이름을 등록해서 자바스크립트 엔진에 변수의 존재를 알린다
2. 초기화<sub>initialization</sub> 단계 :  값을 저장하기 위해 메모리 공간을 확보하고 암묵적으로 `undefined`를 할당해 초기화한다

> 초기화를 진행하는 이유  
초기화 단계를 거치지 않으면 확보된 메모리 공간에 이전에 다른 어플리케이션이 사용했던 값이<sub>garbage value</sub> 남아 있을 수 있기 떄문이다. 암묵적인 초기화를 수행해 이러한 위험으로부터 안전하다


## 값 할당
할당 연산자 =를 사용해, 우변의 값을 좌변의 변수에 할당한다.

<div style="display: flex; flex-grow:wrap; justify-content:space-between; gap:0px 10px">
<div style="flex-grow:1;">
<div class="codebox-title">변수 선언 후 값의 할당</div>

```javascript
let socre;
score = 80;
```
</div>

<div style="flex-grow:1;">
<div class="codebox-title">단축 표현</div>

```javascript
let socre = 80;
```
</div>
</div>

두 코드는 동일하게 동작한다 이는 단축 표현해도 변수 선언과 값의 할당을 2개의 문으로 나누어 각각 실행하는 것을 의미한다  
주의할 점은 변수 선언과 값의 할당의 실행 시점이 다르다는 것이다 **변수 선언은 코드가 순차적으로 실행되는 시점인 런타임 이전에 먼저 실행되지만 값의 할당은 코드가 순차적으로 실행되는 시점인 런타임에 실행된다**

> 변수 선언문이 코드의 선두로 끌어 올려진 것처럼 동작하는 자바스크립트의 특징을 **변수 호이스팅**<sub>variable hoisting</sub>이라 한다.

<div class="codebox-title">변수 호이스팅 예제</div>

```javascript
console.log(score); // undefined

score = 80;         // 2. 값의 할당
let socre;          // 1. 변수 선언

console.log(score); // 80
```
런타임 이전에 변수 선언(1)이 먼저 실행되고 값의 할당(2)는 런타임에 실행된다 따라서 score 변수는 값을 할당하는 시점(2)에는 이미 변수 선언이 완료된 상태이며, `undefined`로 초기화되어 있다. 이후에 새롭게 할당된 숫자 값 80으로 변경(재할당)된다





```toc

```