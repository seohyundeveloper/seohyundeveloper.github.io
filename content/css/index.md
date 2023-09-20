---
emoji: 🍈
title: CSS Layout - 챌린지 도전하기1
date: '2023-09-18 00:18:00'
author: Lani서현
tags: blog CSS flex 
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
  

이렇게 우리가 하는 계산을 컴퓨터가 대신 해주면 어떨가? 하는 생각에 flexbox가 나타나게 되었습니다.  

### 2. Flexbox 사용하는 이점   

레이아웃을 만드는 과정에서 flexbox를 사용하기 전에는 컴퓨터에게 일일히 계산해서
모든것을 명령적으로 이야기 했다면, flexbox를 사용함으로써 컴퓨터 즉 브라우저에게 원하는
것을 말하기만 하는 형태인 선언적으로 바뀌었습니다.  
또한 flexbox를 사용하면서 각각의 item에게 명령할 필요가 없습니다.  
flexbox는 자식 item들을 감싸고 있는 부모 container에 명령을 합니다.  
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
flexbox를 사용하면 위와 같이 코드를 많이 사용하지 않고 간편하게 레이아웃을 
동일하게 만들 수 있습니다.  
또한 브라우저의 크기가 변화하더라도 다른 기타 작업 없이 레이아웃을 유지할 수 있습니다.

### 3. flexbox의 주요 이론  

> 1. 아이템의 레이아웃을 조절하기 위해서는 직속 부모요소에 값을 줍니다.  
>    몇몇 속성은 부모가 아닌 아이템에 직접적으로 값을 주기도 합니다.  
> 2. flexbox에는 두 축이 있습니다. - main axis(주죽) cross axis(교차축)
>    두 축의 위치는 부모요소의 direction에 따라 달라집니다.  
>    예를 들어 direction이 row인 경우 왼쪽에서 오른쪽으로 가는 방향이 main axis가 되고 위에서 아래 방향이 cross axis가 됩니다.  

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

### 4. flexbox의 주요 속성
> 1. flex-direction  
>    아이템의 방향을 결정하며, 옵션은 4가지가 있습니다. (기본값은 row입니다.)   
>    row (수평방향)   
>    column (수직방향)  
>    row-reverse (반대로수평방향)  
>    column-reverse (반대로 수직방향)     
> 2. justify-content  
>    아이템을 main axis를 기준으로 정렬시켜주며, 옵션은 7가지가 있습니다.  
>    flex-start ( flexbox의 시작부분에 아이템이 위치함. )  
>    flex-end ( flexbox의 끝부분에 아이템이 위치함. )  
>    center ( flexbox위 가운데에 아이템이 위치함. )
>    space-between ( 양끝에 아이템이 위치, 나머지 아이템이 공간을 동일하게 나눠서 위치함. )  
>    space-around ( 아이템이 좌우 공간을 동일하게 나눠서 위치함. )  
>    space-evenly ( 아이템의 모든 여백이 동일함. )  
>    stretch ( flexbox의 크기만큼 main-axis방향으로 아이템 크기 늘어남. )
> 3. align-items  
>    <b>아이템</b>을 cross axis를 기준으로 정렬시켜주며, 옵션은 4가지가 있습니다.   
>    stretch ( flexbox의 크기만큼 cross-axis방향으로 아이템 크기가 늘어남. )  
>    flex-start ( flexbox의 시작부분에 아이템이 위치함. )  
>    flex-end ( flexbox의 끝부분에 아이템이 위치함. )  
>    center ( flexbox의 가운데에 아이템이 위치함. )  
> 4. flex-wrap  
>    아이템의 줄바꿈을 바꾸는 속성으로, 옵션은 3가지가 있습니다. (기본값은 nowrap입니다.)
>    nowrap ( 아이템을 줄바꿈 없이 정렬함. - 아이템의 크기를 보장하지 않는다. )  
>    wrap ( 아이템을 크기에 맞춰 정렬함. 줄바꿈 혀용 - 아이템 크기를 보장한다. )  
>    wrap-reverse ( 줄바꿈을 허용하며 아이템을 반대 방향으로 정렬한다. - 아이템 크기 보장한다. )  
> 5. flex-flow  
>    flex-direction과 flex-wrap의 속성을 한번에 나타낼수 있습니다. ( 순서대로 표현하기 )  
>    ```css  
>       예시)  
>       flex-flow : row wrap; // 기본값, 순서에 유의하기!!! 
>    ```  
> 6. align-content  
>    <u>다중라인</u>에서 <b>라인</b>들을 정렬시켜주며, 옵션은 5가지가 있습니다.  
>    align-items와는 라인을 이동시킨다는 점에서 차이가 있습니다.  
>    flex-start ( flexbox의 시작부분에 아이템들이 위치함. )  
>    flex-end ( flexbox의 끝부분에 아이템이 위치함. )   
>    center ( flexbox의 가운데에 아이템들이 위치함. )     
>    space-between ( 양끝에 아이템이 위치, 나머지 아이템이 공간을 동일하게 나눠서 위치함. )   
>    space-around  ( 아이템이 좌우 공간을 동일하게 나눠서 위치함. )  
> 7. gap  
>    아이템들간의 간격을 의미합니다. 옵션은 4가지가 있습니다.    
>    ```css  
>    gap: 20px; -> 상하 좌우 모두 정의된 간격으로 벌어짐.    
>    row-gap: 10px;  -> 좌우만 정의된 간격으로 벌어짐.  
>    column-gap: 30px; -> 상하만 정의된 간격으로 벌어짐.  
>    gap: 30px 10px; -> 위의 내용을 한번에 정의할 수 있습니다.  
>    ```  
> 8. order  
>    아이템 각자의 위치를 정할 수 있습니다. 반응형 디자인에 유용하게 사용할 수 있습니다. 
>    이 속성은 부보에게 주는 속성이 아닌 자식에게 주는 속성입니다.   
>    기본값은 <b>0</b>이고 상대적인 값이기 때문에 음수도 가능합니다.  
> 9. align-self  
>    교차축 정렬을 아이템 개별로 정할 수 있습니다. 이 속성도 자식에게 주는 속성입니다.  
>    flex-start ( 해당 아이템만 교차축에서 맨 위로 정렬됨. )  
>    flex-end ( 해당 아이템만 교차축에서 맨 아래러 정렬됨. )  
> 10. flex-grow ( flex-shink와 함께 사용할 수 있습니다. )  
>     아이템들이 flexbox의 크기를 비율대로 차지하게 할 수 있습니다.  
>     여기서 주어지는 값은 상대적인 값이 됩니다.  
>     기본값은 0이되고, 콘텐츠가 있는 공간만큼만 차지합니다. 
> 11. flex-shink   
>     flexbox가 작아질수록 어떤 아이템이 얼마만큼 더 축소되는지 정할 수 있습니다.  
>     기본값은 1이고 0의 경우는 아이템이 줄어들지 않고 끝까지 유지됩니다.  
>     숫자가 클수록 더 빨리 축소할 수 있습니다. 이 값도 상대적인 값입니다.  
>     반응형으로 작업할 때 어떤것을 먼저 줄어들게 할지를 정할 수 있습니다.  
> 12. flex-basis  
>     아이템의 초기 사이즈를 정할 수 있습니다. 사이즈가 커지기도 하고 작아지기도 합니다.
>     width와 다른 점은 main axis를 가진다는 점입니다.  
>     즉, main axis에 따라 가로가 될 수도 있고, 세로가 될 수도 있습니다.   
> ※ flex: 1 0 500px;    
>     - 위와 같이 flex-grow / flex-shink / flex-basis를 한번에 사용할 수 있습니다. 각각의 값은 위의 순서와 동일합니다.  



