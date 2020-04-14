# TIL
오늘 내가 배운 것들(Today I Learned)   

---------------------------------------

#### 3주차 질문


---------------------------------------

## 표현 디자인(CSS)
<details open>
<summary>11일차 학습</summary>
<div markdown="11">

#### [2D 트랜스폼]
- IE9+ 이상에서 사용가능.
- 회전 - `rotateX(angle)` / `rotateY(angle)` / `rotate(angle)`   
  - degree(각도), turn(턴), radian(라디안)   

  ```css
    transform : rotateX(50deg) rotateY(1.5turn) rotate(1rad);
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
  transition-property : top, transform;
  transition-duration : 0.45s, 0.8s;
  transition-timing-function : ease-in-out, ease;
  transition-deay : 0.4s, 0.4s;
  /*transition : top 0.45s ease-in-out 0.4s, transform 0.8s ease 0.4s;*/
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
#### [보더 이미지]
#### [멀티 컬럼 레이아웃]

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
