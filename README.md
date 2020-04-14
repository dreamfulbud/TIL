# TIL
오늘 내가 배운 것들(Today I Learned)   

---------------------------------------

#### 3주차 질문
- Q. `column-fill`은 무슨 속성인가요? 속성값을 'auto / balance / balance-all' 수정해봐도 차이를 모르겠어요;;

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

<details open>
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

#### [플렉시블 레이아웃 Lecture1]
#### [플렉시블 레이아웃 Lecture2]
#### [플렉시블 레이아웃 Lecture3]

</div>
</details>

---------------------------------------

<details>
<summary>14일차 학습</summary>
<div markdown="14">

#### [그리드 레이아웃 Lecture1]
#### [그리드 레이아웃 Lecture2]
#### [그리드 레이아웃 Lecture3]
#### [그리드 레이아웃 Lecture4]
#### [그리드 레이아웃 Lecture5]

</div>
</details>

---------------------------------------

<details>
<summary>15일차 학습</summary>
<div markdown="15">

#### [그리드 레이아웃 Lecture6]
#### [그리드 레이아웃 Lecture7]
#### [그리드 레이아웃 Lecture8]
#### [그리드 레이아웃 Lecture9]

</div>
</details>
