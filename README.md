# TIL
오늘 내가 배운 것들(Today I Learned)   

---------------------------------------

#### 3주차 질문
- Q. `column-fill`은 무슨 속성인가요? 속성값을 'auto / balance / balance-all' 수정해봐도 차이를 모르겠어요;;
```
A. column-fill 속성은 다단 영역 콘텐츠 흐름의 영향을 받는 방식을 지정하는 속성입니다.
방식은 크게 auto와 balance가 있습니다.
auto는 기본 값으로, 단의 길이가 다른 단의 길이에 따라 서로 다르게 표현될 수 있으며 단이 순서대로 채워집니다.
두 번째로 balance는 단의 높이가 다른 단의 크기에 따라 균형을 이루도록 단이 순서대로 채워집니다.
아래 GitBook에 balance와 auto를 적용한 경우 차이점을 보여주는 예시가 있으니 참고하시기 바랍니다.
https://seulbinim.github.io/WSA/multi-column.html#column-fill-%EC%86%8D%EC%84%B1
```

- Q. `row-reverse` `column-reverse` `order` 속성들을 사용해 순서를 바꾼 경우, 키보드 Tab 진행은 이와 상관없이 마크업 순서로 되는데,
시각적으로 보이는 순서대로 키보드를 진행시키려면 javascript로 변경해야하는건가요?

---------------------------------------

## 표현 디자인(CSS)
<details>
<summary>11일차 학습</summary>
<div markdown="11">

#### [2D 트랜스폼]
- IE9+ 이상에서 사용가능.
- 회전 - `rotateX(angle)` / `rotateY(angle)` / `rotate(angle)`   
  - degree(각도), turn(턴), radian(라디안)   

  ```css
    .class{transform : rotateX(50deg) rotateY(1.5turn) rotate(1rad);}
  ```   

- 크기 - `scaleX()` / `scaleY()` / `scale(x, y)`   

- 이동 - `translateX()` / `translateY()` / `translate(x, y)`   

- 비틈 - `skewX()` / `skewY()` / `skew(x, y)`   

- 중심축 설정 - `transform-origin:50% 50%;` - 기본값

#### [트랜지션]
- IE10+ 이상에서 사용가능.
- `transition-property` 속성
- `transition-duration` 시간
- `transition-timing-function` 타이밍 함수
  - 기본값 : linear / ease / ease-in / ease-out / ease-in-out
  - cubic-bezier 참고 -  [Ceaser] https://matthewlein.com/tools/ceaser
- `transition-delay` 지연시간
- `transition` 속기형
```css
  .sonic{
    transition-property : top, transform;
    transition-duration : 0.45s, 0.8s;
    transition-timing-function : ease-in-out, ease;
    transition-deay : 0.4s, 0.4s;
    /*transition : top 0.45s ease-in-out 0.4s, transform 0.8s ease 0.4s;*/
  }
```

#### [애니메이션]
- IE10+ 이상에서 사용가능.
- `animation-name` 이름
- `animation-duration` 시간
- `animation-timing-function` 타이밍 함수
- `animation-delay` 지연시간
- `animation-direction` 종료 후, 진행 (순/역)방향
  - reverse / alternate / alternate-reverse
  - alternate가 적용될려면 animation-iteration-count 값이 짝수
- `animation-iteration-count` 반복 횟수 (infinite: 무한반복)
- `animation-play-state` 재생/일시정지 설정
  - running:기본값 / paused
- `animation-fill-mode` 시작 전/종료 후 키프레임 설정 (forwards: 유지)
  - none:기본값 / backwards / forwards / both
- `animation` 속기형   

  ```css
  .sonic {
  /*
    animation-name:sonic-running;
    animation-duration:1s;
    animation-timing-function:ease;
    animation-iteration-count : infinite;
    animation-direction:alternate;
    animation-fill-mode:forwards;
    animation-delay:400ms;
  */
    animation:sonic-running 1s ease infinite alternate forwards 0.4s paused;
  }
  .sonic-adventure:active .sonic{
    animation-play-state:running;
  }

  @keyframes sonic-running{
    from{}
    to{
      transform:translateX(740px);
    }
  }
  ```
#### [3D 트랜스폼]
- IE10+ 이상에서 사용가능.
##### 트랜스폼을 적용할 요소에 적용 하는 속성
  * `transform-origin`
  * `backface-visibility`
  * `rotateX()` / `rotateY()` / `rotateZ()` / `rotate3d(x, y, z)`
  * `translateX()` / `translateY()` / `translateZ()` / `translate3d(x, y, z)`
  * `scaleX()` / `scaleY()` / `scaleZ()` / `scale3d(x, y, z)`
  * `skewX()` / `skewY()` / `skew()`

##### 자식 요소를 3D 처리할 부모 요소에 설정
  * `perspective`
  * `perspective-origin`
  * `transform-style: preserve-3d` (요소의 자식이 3D 공간에 배치)   

    ```css
    .album-card {
      position:relative;  cursor: pointer;  float: left;
      width: 340px;  height: 340px;  margin: 30px;
      transition: box-shadow 0.3s ease-in-out;
      transform-style:preserve-3d; /*중요*/
      transform:perspective(1000px);
    }

    .album-card * {
      position:absolute;  top:0;  left:0;
      width: inherit;  height: inherit;
      transition: all 0.8s cubic-bezier(0.230, 1.000, 0.320, 1.000) 0.5s;
    }

    .album-card:hover .album-cover {
      transform: rotateY(180deg) scale(0.85);
    }
    .album-card:hover .album-player {
      transform: rotateY(360deg) scale(0.85);
    }
    .album-cover {}
    .album-player {
      border: none;
      transform: rotateY(180deg);
      backface-visibility:hidden;
    }
    ```
- [실습참고] https://codepen.io/dreamfulbud/pen/PoPqyQq?editors=1100
</div>
</details>

---------------------------------------

<details>
<summary>12일차 학습</summary>
<div markdown="12">

#### [그레디언트]
- IE10+ 이상에서 사용가능.

- 선형 그레디언트 `linear-gradient(angle, start, end)`
  ```css
  body{
    background:linear-gradient(180deg, #f7e763, #fe8201);
    background:linear-gradient(45deg, #f7e763 20%, #45d5bf 60%, #fe8201);

    /*끊어진 형태*/
    background:linear-gradient(
      45deg,
      #f7e763 40%,
      #45d5bf 40%,
      #45d5bf 60%,
      #fe8201 60%,
      #fe8201);
  }
  ```

- 원형 그레디언트 `radial-gradient(shape, start, end)`
  - ellipse(기본값) / circle: 정원
  - `at % %` : 중심 지정
  - farthest-corner(기본값) / closest-side : 가장 먼/가까운 부분까지 그레디언트 효과 적용
  ```css
  body {
    background:radial-gradient(#f7e763, #45d5bf);
      background:radial-gradient(circle at 50% 0, #f7e763 50%, #45d5bf 50%, #fe8201);
    background:radial-gradient(circle closest-side, #f7e763 50%, #45d5bf 50%, #fe8201);
  }
  ```

- 배경 패턴
  ```css
  body {
    background : url('//goo.gl/B6SfbX');
    background-size : 90px;
  }
  ```

- 오버레이 그레디언트
  ```css
  body {
    background:
    linear-gradient(45deg, hsla(12, 100%, 50%, 0.4), hsla(54, 90%, 68%, 0.5)),
    url('//goo.gl/B6SfbX');
    background-size : contain, 90px;
  }
  ```

- 멀티 배경 테크닉 활용
  - 멀티 그레디언트
    ```css
    body {
      background:
      linear-gradient(217deg, rgba(255,0,0,0.45), rgba(255,0,0,0) 65.70%),
      linear-gradient(127deg, rgba(0,255,0,0.45), rgba(0,255,0,0) 65.70%),
      linear-gradient(336deg, rgba(0,0,255,0.45), rgba(0,0,255,0) 65.70%),
      url('//goo.gl/B6SfbX');
      background-size : 100%,100%, 100%,140px;
    }
    ```
    ```css
    body {
      background:
      radial-gradient(circle at 50% 0, rgba(255,0,0,0.45), rgba(255,0,0,0) 65.70%),
      radial-gradient(circle at 6.7% 75%, rgba(0,255,0,0.45), rgba(0,255,0,0) 65.70%),
      radial-gradient(circle at 93.3% 75%, rgba(0,0,255,0.45), rgba(0,0,255,0) 65.70%),
      url('//goo.gl/B6SfbX');
      background-size : 100%,100%, 100%,140px;
    }
    ```

  - 반복 그레디언트 (패턴배경 응용)
    ```css
    body {
      background:repeating-linear-gradient(
        -45deg, red, red 10px, yellow 10px, yellow 20px
      );
    }
    ```
    ```css
    body {
      background:repeating-radial-gradient(
        circle at 50% 15%, red, red 10px, yellow 10px, yellow 20px
      );
    }
    ```

#### [보더 이미지]
-  IE 11+ 이상에서 사용가능
- border-image : source [slice / width / outset] repeat];
  - `border-image-source: url();` 필수요소
  - `border-image-slice`
    - 이미지의 top/right/bottom/left 가장자리 오프셋을 설정(최대 4개) - padding,margin과 같은 방식
    - 보더 이미지를 9개 영역으로 나눌 수 있음(px단위 사용X, %사용)   

  - `border-image-width`
    - 요소의 top/right/bottom/left 테두리 이미지 너비를 설정(최대 4개)
    - 실제 테두리의 너비는 영향을 받지 않고 이미지는 맨 위에 배치.
    - border-image 너비가 border-width 보다 클 경우 채우기 영역 또는 내용 영역을 포함.
    - **단위 없는 값은 요소의 테두리 너비의 배수로 해석**
    - 테두리 이미지 너비 = 테두리 너비 (기본)   

  - `border-image-outset`
    - 테두리 이미지를 주어진 값만큼 패딩(안쪽) 영역을 설정(최대 4개)
    - 단위 없는 값을 사용할 경우, 요소의 테두리 너비에 곱하여 오프셋 처리

  - `border-image-repeat` : stretch(기본값) / repeat / round / space

  ```CSS
  .class{
    /*슬라이스 10px 설정, 가장자리 섹션 stretch 사용*/
    border-image:url('imageUrl') 10;

    /*각 테두리 방향에서 5% 조각 이미지 사용, 가장자리 반복 설정*/
    border-image:url('imageUrl') 5% round;

    /*슬라이스 오프셋 - 순서 : top right bottom left*/
    border-image:url('imageUrl') 10 20 30 40;

    /*테두리를 2배 큰 border-width 값으로 크기 조정*/
    border-image:url('imageUrl') 10/2 repeat;

    /*테두리를 2배 큰 border-width 값으로 크기 조정
    + 여백 테두리는 1배 border-width 값으로 설정*/
    border-image:url('imageUrl') 5 / 2 / 1;

    /*4개의 가장자리마다 각기 다른 설정*/
    border-image:url('imageUrl') 5 8 6 10 / 1 2 1 3 / 0 1 .5 .5;
  }
  ```

- [참고] https://codepen.io/dreamfulbud/pen/VwvvrRj


#### [멀티 컬럼 레이아웃]
-  IE 10+ 이상에서 사용가능
- **유의** 이미지 잘림 현상 발생.
- 컬럼 개수 또는 폭 설정
  - `column-count`, `column-width`, `columns` (속기형 작성법)   

    ```
    [예시]
    columns: 12em;       // column-width: 12em; column-count: auto
    columns: auto 12em;  // column-width: 12em; column-count: auto
    columns: 2;          // column-width: auto; column-count: 2
    columns: 2 auto;     // column-width: auto; column-count: 2
    columns: auto;       // column-width: auto; column-count: auto
    columns: auto auto;  // column-width: auto; column-count: auto
    columns: 12 320px;   // column-width: 320px; column-count: 12
    ```
- 컬럼 간격 또는 구분 선 설정
  - `column-gap`
  - `column-rule`
    - `column-rule-color`, `column-rule-style`, `column-rule-width`   


  ```CSS
    .magazine-section {
     margin : 6rem 0;
     /*column-count: 3;
     column-width:320px;*/
     columns: 12 20em;
     column-gap : 2em;
     column-rule: 1px dotted #ccc;
    }
  ```

- 컬럼 병합
  - `column-span`
  ```CSS
    .magazine-headline {column-span:all; }
  ```

- 컬럼 채우기
  - `column-fill` : auto / balance(기본값) / balance-all



</div>
</details>

---------------------------------------

<details>
<summary>13일차 학습</summary>
<div markdown="13">

#### [플렉시블 레이아웃]
- IE 10+ 이상에서 사용가능
- Flexbox는 페이지의 한 방향(x, y축)으로 요소를 효율적으로 배치 할 수 있도록 설계

##### flex-container 속성
- `display:flex`
  - flex container / flex items로 구성
  - 직계 **자식** 요소만 flex-item이 됨.
  - flow axis - 주축(main axis), 교차축(cross axis) - start / center / end   

- `flex-direction`
  - row(기본값) / column / row-reverse / column-reverse
  - direction 설정에 따라 주축 방향 변경됨.   

- `justify-content` 주축에 대한 정렬.
  - flex-start / center / flex-end
  - space-between : 시작과 끝을 제외하고 여백 균등 배분
  - space-around : item 요소 좌우 동일한 여백
  - space-evenly : 시작~끝 간격 모두 동일하게   

- `flex-wrap`
  - nowrap(기본값) / wrap / wrap-reverse
  - flex-item 요소는 flex-shrink값이 1로 기본 설정되어있기 때문에 너비값이 있다고 해도 부모요소인 flex-container에 맞춰 자동으로 설정됨.

- `align-items` - 요소 정렬
  - flex-start / flex-end / center / baseline / stretch

- `align-content` - 덩어리 정렬.
  - flex-start / flex-end / center / space-between / space-around / space-evenly / stretch

- `flex-flow` 속기형
    ```CSS
    .item { flex-flow: direction wrap; }
    .container { flex-flow:row nowrap; }
    ```   


##### flex-item 속성
- `flex-basis` : flex-item은 width 사용 X   

  ```css
    .item{flex-basis: 100px;}
  ```

- `align-self` - 다른 아이템과 상관없이 독자적으로 정렬.
  - auto / flex-start / flex-end / center / baseline / stretch   

- `flex-grow` - 요소 키움
  - 기본값 0
  - 1 : 자동으로 늘어나 flex-container에 맞춤   

- `flex-shrink` - 요소 축소
  - 기본값 1 : 자동으로 축소되어 flex-container에 맞춤   
  - 0 : width값 줄어들지 않음.

- `flex` 속기형
  ```CSS
    .item { flex: flex-grow [flex-shrink] [flex-basis]; }
    .item { flex: 0 0 20%}
  ```

- `order`
  - 기본값 0
  - 숫자가 작을수록 우선 배치
  - 동일한 값을 가지고 있다면 마크업된 순서로 우선권을 가짐.

- **가운데 정렬** (텍스트 세로-중앙 정렬 가능!!!!)
  ```CSS
    .item {display:flex; justify-content:center; align-items:center;}
  ```


- [참고 예제]
  - https://codepen.io/dreamfulbud/pen/WNQrvqG?editors=1100
  - https://codepen.io/dreamfulbud/pen/VwvevXY

</div>
</details>

---------------------------------------

<details open>
<summary>14일차 학습</summary>
<div markdown="14">

#### [그리드 레이아웃]
- IE 10+ 이상에서 사용가능   

##### 01-1. CSS 레이아웃의 역사
1. 레이아웃 도구가 없던 시절
  - 레이아웃을 위한 디자인 방법 없이 타이포 그래피와 정렬만 가능.

2. 테이블 기반 레이아웃
  - 본 목적과는 다르게 테이블로 레이아웃을 만들던 시대.
  - 여백을 투명한 gif 이미지로 만듦.
  - 의미 상실, 접근성 부재

3. 프레임 기반 레이아웃
  - 여러 장의 HTML 페이지를 'frame'을 사용하여 한 페이지에 결합하여 레이아웃을 만듦.

4. 플로트, 포지션 기반 레이아웃
  - float, clear, position, Box Model 등을 사용하여 레이아웃을 만듦.
  - 브라우저 특성(버그)에 기반엔 비논리적 기법이 난무.

5. 플렉스 박스 레이아웃
  - 플렉시블 박스 모델을 사용하면 컨텐츠를 균등하게 분배하고 사용가능한 공간을 활용할 수 있음.(1차원)
  - **X 또는 Y축. 한쪽 방향으로만 설정 가능** 한 자유도가 낮은 레이아웃 기법.

6. **CSS 그리드 레이아웃**
  - HTML 마크업 순서와 무관하게 내부에 포함된 자식 아이템을 그리드 내부 어디든 위치 시킬 수 있음(2차원)
  - **X 그리고 Y축. 양쪽방향 모두 설정 가능** 한 자유도가 높은 레이아웃 기법.   

##### 01-2. W3C 표준 기술 결정 절차
1. WD(Working Draft)
2. **CR(Candidate Recommendation)** : 워킹그룹 결정, 책임자 승인
3. PR(Proposed Recommendation)
4. REC(W3C Recommendation)
- 현재 CSS Grid는 CR 상태

##### 01-3. Autoprefixer 도구
- [Autoprefixer CSS online] https://autoprefixer.github.io

---

##### 02. CSS Grid 용어(Terminology)
- Grid
  - HTML 요소에 display 속성값으로 grid를 설정하면 grid-container가 되며, row, column을 가진다.
  - 포함된 자식 요소는 그리드 grid-item이 된다.
- Grid 라인 (lines) : Grid를 행(rows)/열(columns)로 나누는 수평, 수직 선.
- Grid 셀 (cell) : Grid를 구성하는 단일 유닛(single unit).
- Grid 영역 (area) : Grid 라인이 감싸는 사각형 영역. Grid 영역은 여러 개의 Grid 셀을 포함할 수 있음.
- Grid 트랙 (track) : 2개의 그리드 라인 사이 공간. 이 공간은 수평/수직 방향 모두.
- Grid 행 (로우, row) : 1개의 Grid 수평 트랙.
- Grid 열 (컬럼,column) : 1개의 Grid 수직 트랙.
- 거터 (Gutter) : Grid 행과 열 사이 공간.
  - `grid-gap` 속성으로 제어

- [참고] https://codepen.io/dreamfulbud/pen/GRpooGx

---
##### 03. grid, row/column 템플릿 설정
- `gird`
  - `block-grid` / `inline-grid` / `subgrid`(CSS Lv2에서 지원예정)   

    ```css
    .block-grid { display: grid; }
    .inline-grid { display: inline-grid; }
    ```
  - overflow 속성은 그리드 컨테이너 적용 가능.
  - float, clear, column, vertical-align 속성은 그리드 컨테이너 요소에 적용되지 않음.
  - grid 공부 시 firefox 브라우저 사용. grid의 정보를 시각적으로 확인할 수 있음.

- `row/column`
  - 공백으로 구분된 값 리스트를 해석하여 그리드 행(row), 열(Column)을 설정. 각 값은 트랙 크기를 말함.
  - `<track-size>` : 그리드에서 사용 가능한 공간의 길이(px, rem, em, %, `fr` 등)
  - `<line-name>` : 사용자가 설정한 임의의 선 이름.   

    ```CSS
    .grid{
      display: grid;
      /* 2행 */
      grid-template-rows:10rem 10rem;
      /* 3열 */
      grid-template-columns: 10rem auto 10rem;
    }
    ```

---

##### 04. gutters, fr 단위, repeat() 함수사용법
- gutters
  - grid-row-gap /  grid-column-gap / grid-gap(속기형)
  ```CSS
  .grid{
      display: grid;
      /*
      grid-row-gap:2rem;
      grid-column-gap:4rem;
      */
      grid-gap:2rem 4rem;
  }
  ```

- `fr`(Fraction) 단위
  - 컨테이너 너비를 기준으로 비율 단위
  ```CSS
  .grid{
      display: grid;
      grid-template-rows:1fr 4fr;
      grid-template-columns:1fr 2fr 3fr;
  }
  ```
- `repeat()` 함수
  - repeat(반복횟수(양수), 그리드 트랙 리스트(배열))
  ```CSS
  .grid{
      display: grid;
      grid-template-rows:repeat(2, 1fr);
      grid-template-columns:repeat(3, 1fr 2fr); /* (1fr 2fr) (1fr 2fr) (1fr 2fr) */
  }
  ```

---

##### 05. minmax() 함수 사용법, 암시적으로 row/column 자동 행/열 길이 설정
- `minmax()` 함수 : 최소값과 최대값 지정
  - minimax(최소값, 최대값)
  ```CSS
  .grid{
      display: grid;
      grid-template-rows: repeat(2,minimax(20px, auto));
      grid-template-columns:minmax(30px, auto) repeat(3, 1fr);
  }
  ```

- 암시적으로 row/column 자동 행/열 길이 설정
  - `grid-auto-rows`/ `grid-auto-column`
  - 암시적인 그리드 행/열 트랙 크기를 자동으로 설정
  - min-content : 컨텐츠에 맞게
  ```CSS
  .grid{
      display: grid;
      grid-template-rows: repeat(2,minimax(20px, auto));
      grid-template-columns:minmax(30px, auto) repeat(3, 1fr);
      grid-auto-rows: minmax(10rem, auto);
      grid-auto-columns: minmax(10rem, auto);
  }
  ```


</div>
</details>

---------------------------------------

<details>
<summary>15일차 학습</summary>
<div markdown="15">

#### [그리드 레이아웃]
##### 06. 그리드 라인 인덱스를 사용하여 아이템 위치 설정
##### 07. 오더 속성을 사용한 아이템 순서 변경 / 그리드 영역 / 그리드 템플릿 영역을 사용하여 아이템 위치 설정
##### 08. 그리드 흐름 자동 배치 알고리즘 활용
##### 09. 아이템들 & 콘텐츠 행, 열 방향 정렬 / 아이템 개별 행, 열 방향 정렬 / grid 속기형 속성 활용법
</div>
</details>
