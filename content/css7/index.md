---
emoji: 🍈
title: CSS Layout - 챌린지 도전하기7
date: '2023-09-26 18:28:00'
author: Lani서현
tags: blog CSS layout 
categories: CSS 
---

## 챌린지 설명

CSS Layout 챌린지를 도전하면서 배운것들을 기록합니다.   

### 1. BEM 방법론  

`BEM(Block, Element, Modifier)`은 네이밍 방법론 중 하나입니다. 프로젝트가 크면 클수록
네이밍 규칙은 중요하게 작용하기 때문에 공부할 필요가 있습니다.  
BEM의 가장 큰 특징은 `ID를 절대 사용하지 않는다는 점`입니다.

### 2. BEM의 장점  

 > + 목적과 기능을 명확히 전달합니다.  
 > + 요소의 구조를 효율적으로 전달합니다.  
 > + css 명시도를 항상 낮은 수준으로 유지하기 때문에 구체성으로 인한 코드의 길어짐을 방지할 수 있습니다. 

### 3. Block (블록)  

block(블록)은 페이지 전체 Element(요소)를 의미하거나 하위 Element(요소)를 감싸는 컨테이너를 의미합니다. 즉 독립적인 의미를 가지는 추상화된 컴포넌트 입니다.  
#### 규칙  
> 문자, 숫자, 대시(-)로 구성됩니다.
> ```html  
> <div class="block"></div>
> <div class="box1"></div>
> <div class="list-container"></div>
> ```
> 여기서 `block, box1, list-container` 모두 블록 역할을 합니다.  
> 클래스를 적용할 수 있는 DOM노드라면 뭐든 블록이 될 수 있습니다.  
> ```css
> // 사용법에 맞는 구조
> .block {
>   color: #cccccc;  
> }
> // 사용법에 어긋나는 구조
> div.block { ... }  
> #id.block { ... }
> ````
> css의 경우 `클래스 이름만` 사용해야 하며, `태그이름, ID중첩 사용을 금지`하고 있습니다.  
> 다른 블록에 대한 종속성이 없습니다.  

### 4. Element (요소)  

블록의 구성요소이자 하위요소입니다. 모든 요소는 상위 블록과 연결되어 있습니다.  
#### 규칙  
> 문자, 숫자, 대시(-) 및 밑줄(_)로 구성될 수 있습니다.  
> ``` html
> <div class="block">
>   <div class="block__elem"></div> 
> </div>
> <div class="box">
>   <div class="box__content"></div> 
> </div>
> <div class="wrapper">
>   <div class="wrapper__item"></div> 
> </div>
> ```

> ```css
>  // 사용법에 맞는 구조
> .box__content {
>   background-color: aqua;  
> }
> // 사용법에 어긋나는 구조
> .box .box__content {
>   background-color: aqua;  
> }
> div.box__content {
>   background-color: aqua;  
> }
> ```
> css의 경우 `클래스 이름만` 사용해야 하며, `태그이름, ID중첩 사용을 금지`하고 있습니다.   

### 5. Modifier (수정자)  

Block이나 Element의 속성 (상태 또는 행동)을 담당합니다. 생긴게 조금 다르거나 다르게 동작하는 블록이나 엘리먼트를 만들때, `추가`하는 방식으로 사용합니다.   

#### 규칙  
> 수정자의 이름은 문자, 숫자, 대시(-)및 및줄 (_)로 구성될 수 있습니다. 
> `블록이름--수정자이름` 또는 `요소이름--수정자이름` 형태로 작성합니다.  
> ```html
>  <!--잘 사용된 경우-->
> <div class="block block--size--big">
>   <div class="block__elem block__elem--mod"></div> 
> </div>
> ```
> 블록 혹은 요소의 클래스는 `그대로 두고` 수정자를 추가해 줍니다.
> ```html
>  <!--잘못 사용된 경우-->
> <div class="block--size--big">
>   <div class="block__elem--mod"></div> 
> </div
>```

※ Hierarchy 구조대로 이름을 작성하는 것이 BEM이 아닙니다.  
   -> `컴포넌트 단위`로 Block 레벨로 이름을 작성하는 것이 좋습니다.