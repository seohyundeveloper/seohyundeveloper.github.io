---
emoji: 🍈
title: CSS Layout - 챌린지 도전하기6
date: '2023-09-24 02:28:00'
author: Lani서현
tags: blog SCSS 
categories: CSS 
---

## 챌린지 설명

CSS Layout 챌린지를 도전하면서 배운것들을 기록합니다.    

### 1. SCSS 란  

SCSS는 CSS를 좀 더 생산적으로 사용하기 위해서 CSS를 확장한 언어 입니다.  
하지만 브라우저는 SCSS를 이해하지 못합니다. 그래서 SASS로 SCSS 코드를 처리해서 브라우저가 이해할 수 있는 CSS로 만드는 작업을 해야 합니다.  
우리가 작성한 SCSS 코드를 브라우저가 이해할 수 있도록 변경하기 위해서는 Vite, Webpack,Gulp 같은 프로그램이 필요합니다.   

### 2. SCSS 사용이유  

예전에는 CSS에서 변수를 사용하고 싶다면 SCSS를 사용해야 했지만, 지금은 CSS만으로도 가능합니다. 이제는 CSS 변수는 표준이 되었고, 모든 브라우저에서 이해할 수 있습니다.  
하지만 아직 CSS에는 nesting, mix-in, extend 등의 기능은 없습니다. 

SCSS의 변수사용 예  

```scss
  $bgColor : red;  // SCSS에서 변수를 정의하는 형태
 
  .child {
    background-color: $bgColor;  // SCSS에서 변수를 사용하는 형태  
  }
```

CSS의 변수사용 예  

```css
  :root {
    --bgColor: red;  // CSS에서 변수를 정의하는 형태
  }

  .child {
    background-color: var(--bgColor);  // CSS에서 변수를 사용하는 형태  
  }
```

### 3. SCSS 설치 및 사용방법  

여기서는 Vite를 이용하는 방법을 알아보도록 하겠습니다.  
Vite를 사용하여 SCSS를 CSS로 변경하는 작업을 하기 위해서는 우리가 사용하는 경로에 알려줘야 합니다.  

```
 // 우리가 작업하는 경로의 터미널에서 아래와 같은 npm명령어 실행.
 npm add -D sass
```  

이렇게 해주면 우리가 사용하는 IDE에서 SCSS를 사용할 수 있습니다.  
우리가 모든 작업을 끝내고 프로젝트를 배포하고 싶을때, 작업중 인것을 중지하여 주고, npm run build를 진행하여 줍니다.  
Vite가 배포를 위해서 dist폴더를 생성하고, 그 안에서 index.html파일을 확인할 수 있는데 그 안에서 stylesheet가 css파일 형태로 변환되어 있습니다. 이러한 과정을 Compile이라고 합니다.  
바로 이 dist폴더가 사용자에게 제공되는 폴더 입니다.  

### 4. SCSS의 주요 속성들  
> nesting (중첩기능)    
>  상위 선택자의 반복을 피하고 좀 더 편리하게 구조를 작성할 수 있어서 사용합니다.  
>  아래와 같은 구조를 SCSS nesting 기능을 사용하면 코드를 줄일 수 있습니다.  
>
>```css
> ul {
>   list-style-type:none;
>   padding: 0;
>   display: flex;
>   gap: 10px;
> }
>
> ul li {
>   background-color: tomato;
>   color: white;
>   padding: 5px 10px;
>   border-radius: 7px;
>  }
>
> ul li:hover {
>   opacity: 0.8;
> }
>
> ul li:hover a {
>   color: gray;
> }
>
> ul li a {
>   text-decoration: none;
>   color: white;
>   text-transform: uppercase;
> }
>```
> 아래의 내용은 scss로 nesting 적용해서 작성한 스타일 입니다.  
> 확실히 위의 코드보다 가독성도 좋고 코드의 길이도 짧아졌습니다.  
>```scss
> ul {
>   list-style-type:none;
>   padding: 0;
>   display: flex;
>   gap: 10px;
>   li {
>     background-color: tomato;
>     color: white;
>     padding: 5px 10px;
>     border-radius: 7px;
>     &:hover {  // &은 위의 요소를 참조함을 의미함.
>       opacity: 0.8;
>       a {
>         color: gray;
>       }
>     }
>     a {
>       text-decoration: none;
>       color: white;
>       text-transform: uppercase;
>     }
>   }
> }
>```
> body부터 모든곳에 nesting을 적용하는 것은 적절하지 못하다.  
> 컴포넌트에 nesting을 적용하는 것이 좋습니다.   

> @extend (상속을 의미함.)
> 클래스 선택자의 모든 스타일을 동일하게 가져야 하지만 부분적으로 다른 경우가 발생합니다.  
> 이때 CSS의 경우에는 다중클래스를 사용하거나 CSS공통으로 사용하는 속성을 모아서 사용하는 경우가 
> 많습니다. 이럴때 @extend를 사용하면 편리하게 사용할 수 있습니다.  
> 하지만 미디어쿼리 내에서는 실행되지 않는 단점이 있어서 반응형 웹이나 모바일에서 사용을 권장하지 않습니다.  
>
>```scss
> %alert {  // 공통으로 사용되는 스타일 정의해줌. 이코드는 최종코드에 보이지 않음.
>   margin: 10px;
>   padding: 10px 20px;
>   border-radius: 10px;
>   border: 1px dashed black;
> }
> 
> .success {
>   @extend %alert; // 공통으로 적용시킬 부분에 적용함.
>   background-color: green; // 부분적으로 다른 부분만 스타일해줌.
> }
> 
> .error {
>   @extend %alert; // 공통으로 적용시킬 부분에 적용함.
>   background-color: red; // 부분적으로 다른 부분만 스타일해줌.
> }
>```

> @mixin (믹스인)  
> 함수와 비슷한 동작을 하는 SCSS문법으로 재사용할 CSS 스타일 그룹 선언을 정의하는 기능을 합니다.
> @mixin에 인자를 사용하면 다양한 스타일을 사용할 수 있습니다.  
> 
>```scss
> @mixin alert($bgColor, $borderColor) {  // $bgColor은 변수 개념임!!! 인수는 여러개를 보낼수 있음
>   background-color: $bgColor;  // 배경색에 인자를 받아와서 처리해줌.
>   margin: 10px;
>   padding: 10px 20px;
>   border-radius: 10px;
>   border: 1px dashed $borderColor;
> }
> 
> .success {
>   @include alert(green, red); // green, red이라는 인수를 넘겨줌.
> }
> 
> .error {
>   @include alert(red, green); // red, green라는 인수를 넘겨줌.
> }
>```

### 5. 반응형에서 사용하는 @mixin 과 @media query  

> mixin에 클래스마다 다른 content를 전달하는 방법은 다음과 같습니다.  
>
>```scss
> @mixin alert($bgColor, $borderColor) {
>   background-color: $bgColor;
>   margin: 10px;
>   padding: 10px 20px;
>   border-radius: 10px;
>   border: 1px dashed $borderColor;
>   @content; 
> }
> 
> .success {
>   @include alert(green, tan) {
>     font-size: 12px;  // 이 부분이 믹스인의 @content로 전달되는 부분임.
>   };
> }
> 
> .error {
>   @include alert(red, lime) {
>     text-decoration: underline;  // 이 부분이 믹스인의 @content로 전달되는 부분임.
>   };
> }
> 
> .waring {
>   @include alert(yellow, blue) {
>     text-transform: uppercase  // 이 부분이 믹스인의 @content로 전달되는 부분임.
>   };
> }
>```
>
>mixin에 클래스마다 다른 content를 전달하는 방법은 우리가 반응형 페이지를 만들때 유용합니다. 
>먼저 화면의 크기에 따른 변수들을 선언해줍니다. 미디어쿼리를 작성할 때 변수로 선언한 값들을 중단점으로 이용하면 손쉽게 반응형을 만들 수 있습니다.  
>아래 방식을 참고하면 브라우저의 크기에 따른 반응형을 쉽게 구현할 수 있습니다. 
>
>```scss
> $breakpoint-sm: 480px;
> $breakpoint-md: 768px;
> $breakpoint-lg: 1024px;
> $breakpoint-xl: 1200px;
> 
> @mixin smallDevice {
>   @media screen and (min-width: $breakpoint-sm) {  // 중단점으로 이용
>     @content;
>   }
> }
> 
> @mixin mediumDevice {
>   @media screen and (min-width: $breakpoint-md) {  // 중단점으로 이용
>     @content;
>   }
> }
> 
> @mixin largeDevice {
>   @media screen and (min-width: $breakpoint-lg) {  // 중단점으로 이용
>     @content;
>   }
> }
> 
> @mixin xlDevice {
>   @media screen and (min-width: $breakpoint-xl) {  // 중단점으로 이용
>     @content;
>   }
> }
> 
> body {
>   @include smallDevice {
>     background-color: blue;  // @content의 내용
>   }
>   @include mediumDevice {
>     background-color: teal;  // @content의 내용
>   }
>   @include largeDevice {
>     background-color: pink;  // @content의 내용
>   }
>   @include xlDevice {
>     background-color: yellow;  // @content의 내용
>   }
> }
>```

