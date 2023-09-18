---
emoji: 🍈
title: CSS Layout - 챌린지 도전하기
date: '2023-09-18 00:18:00'
author: Lani서현
tags: blog gatsby theme 개츠비 테마
categories: CSS 
---

## 챌린지 설명

CSS Layout 챌린지를 도전하면서 배운것들을 기록합니다.

### 1. Flexbox가 나오게 된 배경

웹페이지를 생성할때 레이아웃을 만든다는게 쉬운일이 아닙니다.  
아래와 같이 flexbox를 사용하지 않고 3개의 박스를 한 화면에 나란히 배치시켜 보도록 하겠습니다.

### 예시 )  

 ![사진](./layout1.png) 
  
### [HTML]  

```html
//HTML 파일에서
<body>
  <div class="box"></div>
  <div class="box"></div>
  <div class="box"></div>
</body>
```

### [CSS]  

```css
//CSS 파일에서
  .box{
    width:200px;
    height:200px;
    background-color:tomato;
  }

  .box:first-child {
  margin-right: 20%;
  }

  .box:last-child {
    margin-left: 20%;
  }
```  
  
px을 사용하지 않고 나름 반응형에 적용한다고 %를 사용하여 작업해보았습니다.  
또다른 방식의 { float: left; } 를 이용해서 사용해도 또다시 명령적으로 margin을 
사용할 수 밖에 없었습니다.  
게다가 브라우저의 크기가 너무나도 다양하기 때문에 flexbox를 사용하지 않고 레이아웃을
만드는 일은 엄청난 시간과 노력을 요구합니다.
  

이렇게 우리가 하는 계산을 컴퓨터가 대신 해주면 어떨가?  
하는 생각에 flexbox가 나타나게 되었습니다.  

### 2. Flexbox 사용하는 이점   

레이아웃을 만드는 과정에서 flexbox를 사용하기 전에는 컴퓨터에게 일일히 계산해서
모든것을 명령적으로 이야기 했다면, flexbox를 사용함으로써 컴퓨터 즉 브라우저에게 원하는
것을 말하기만 하는 형태인 선언적으로 바뀌었습니다.
또한 flexbox를 사용하면서 각각의 item에게 명령할 필요가 없습니다.
flexbox는 자식 item들을 감싸고 있는 부모 containerㅇ에 명령을 합니다.
위의 예시에서 부모 container는 body 태그입니다.

### [CSS]  

```css
  body {
    display: flex;
    justify-content: space-between;
  }

  .box {
    width: 200px;
    height: 200px;
    background-color: tomato;
  }
```  
flexbox를 사용하면 위의 방식처럼 많은 코드를 사용하지 않고도 간편하게 레이아웃을 
동일하게 만들 수 있습니다.  
또한 브라우저의 크기가 변화하더라도 다른 기타 작업 없이 레이아웃을 유지할 수 있습니다.

### 3. flexbox의 주요 이론  

> 1. 아이템의 레이아웃을 조절하기 위해서는 직속 부모요소에 값을 줍니다.
> 2. flexbox의 여러 요소 - flex-direction, justify-content, align-items  
> 3. flexbox에는 두 축이 있습니다. - main axis(주죽) cross axis(교차축)
>    두 축의 위치는 부모요소의 direction에 따라 달라집니다.
>    예를 들어 direction이 row인 경우 왼쪽에서 오른쪽으로 가는 방향이 main axis가 되고 위에서 아래 방향이 cross axis가 됩니다.
> 4. justify-content의 경우 아이템을 main axis에서 정렬시켜 줍니다.   
>    align-items의 경우 아이템을 cross axis에서 정렬시켜 줍니다.  

### [HTML] 

```html
  <body>
    <div class="parent">  <-- parent가 부모요소 
      <div class="box"></div>
      <div class="box"></div>
      <div class="box"></div>
    </div>
  </body>
```  

### [CSS] 

```css
  .parent {
    display:flex;  // 아이템을 나란히 배열함.
    flex-direction: row; // 아이템을 배열시키는 방향 row : 가로, column : 세로
    gap: 10px;   // 아이템 사이에 간격을 나타냄.
  }

   .box {
    width: 200px;
    height: 200px;
    background-color: tomato;
  }
```



