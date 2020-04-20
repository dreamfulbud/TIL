# TIL
오늘 내가 배운 것들(Today I Learned)   

---------------------------------------

#### 4주차 질문
- 실습예제에서 사용한 CSS `:root` / `var()` 는 처음 보는데.. 어떠한 규칙으로 사용하는 건가요? 사용법에 대해 좀더 설명부탁드립니다!
  ```CSS
  :root {
    --chrome__background-color: #f0f0f0;
    --chrome-head__bottom-color: #dfdfdf;
    --chrome-head__circle-color: #ccc;
    --bg-image: url("이미지경로");
  }
  .background{
    background:var(--bg-image) no-repeat center;
  }
  ```
---------------------------------------

## 반응형 디자인(RWD)
<details open>
<summary>16일차 학습</summary>
<div markdown="16">

### 반응형 웹이란?
- 테크놀로지의 발전으로 월드 와이드 웹은 데스크톱을 벗어나, 세상 모든 기기에서 이용 가능해졌다.
- 멀티 디바이스를 넘어 우리가 만들어야할 서비스를 이루는 콘텐츠와 컨텍스트에 관한 이야기
- 테크놀로지의 발전은 디자인 바운더리를 변경시킴. 제한된 환경에서 벗어나 무한한 환경으로 진화되고 있는 세상.   

##### ▷ 콘텐츠는 물과 같다
  - 동일한 콘텐츠를 다른 모양에 담을 뿐. 실제 컨텐츠가 변형된것은 아님.   

##### ▷ 반응형 웹 시대를 위한 디자인
  - 각기 다른 기기의 다른 비율과 해상도를 먼저 이해한 뒤, 스케치, 프로토타입, 시각화 테스트 등을 진행해야한다.
  - 우리가 해야할 일은 **미래 친화적인 디자인 생태계를 만드는 것.**   

##### ▷ 반응형 웹 디자인이란?
  - 반응형 웹이 의미하는 바는 서비스를 디자인 하는 과정에 사용자의 환경(스크린 사이즈, 플랫폼, 회전 방향 등)을 고려하여 등답할 수 있도록 제작하는것.

##### ▷ 반응형 웹 시대의 서막
  - Ethan Marcotte : Responsive Web Design - A list apart (2010.5.25)
    ```
      디바이스마다 콘텐츠를 감추거나 격리시키는 것보다는,
      각 기기의 경험을 맞춰 최적화된 뷰를 사용자에게 제공하여
      콘텐츠를 효율적으로 담는 것이 우리가 수행해야 할 일입니다.
                                        - Ethan Marcotte  -
    ```


### 콘텐츠 구성
- 반응형 웹 프로젝트를 시작하기 전 무엇을 고려하고, 알아야 할까?
  - 콘텐츠 전략(Contents strategy)
  - 유연한 그리드 레이아웃(Flexible grid layout)
  - 유연한 이미지/미디어(Flexible images and media)
  - 디바이스 픽셀 밀도(Device Pixel Density)
  - 중단점/미디어 쿼리(Breakpoint and Media queries)

##### ▷ 콘텐츠 전략
  - 콘텐츠에 대한 사전 분석 없이 좋은 서비스는 제작할 수 없다. 각 뷰에서 그려질 콘텐츠 구조를 치밀하게 분석하지 않고는 좋은 사용자 경험을 제공하기 어렵다.

##### ▷ 콘텐츠 구성
  - 고정된 가로폭과 해상도에서 콘텐츠가 영구적으로 자리 잡았던 디자인은 과거의 것이 되었다. 다양하게 변화하는 가로폭과 해상도에 최적의 경험을 제공할 수 있는 무용술(choreography)이 필요하다.

##### ▷ 콘텐츠 쌓임
  - 화면 폭이 줄어들 경우 콘텐츠가 쌓이는 것은 불가피. 화면 폭이 작은환경에서 먼저 표시되는 컨텐츠가 가장 중요한 콘텐츠가 아닐 수도 있다.

##### ▷ 콘텐츠 순서
  - 콘텐츠가 쌓이는 구조의 레이아웃이 아니라, 주요 콘텐츠가 보조 콘텐츠보다 우선적으로 화면에 보야져야 한다.
  - 화면 크기가 작은 모바일 환경에서 우선적으로 보여(읽혀)져야 할 콘텐츠가 무엇인지 고려해야한다.

##### ▷ 콘텐츠 맞물림
  - 폭이 좁고 길쭉한 모양의 뷰에서 각 콘텐츠 사이에 맞물리며 접히는 구조로 콘텐츠가 접힘. 상황에 따라서는 순서가 뒤섞이는 구조로 보여질 경우도 있다.

##### ▷ 플렉시블 박스
  - 콘텐츠 중심 전략, 콘텐츠 구성(안무법) 등을 원활하게 구현하기 위한 새로운 레이아웃 기술이 요구됨에 따라 탄생하게 된 레이아웃 모듈.



### 유연한 그리드
- 유연한 그리드(Fluid Grid)는 일관되게 콘텐츠를 구성하지만, 디스플레이 사이즈에 따라 크기와 위치가 변경된다.
- 유연한 그리드를 구현하는 방법은 고정 그리드를 기반으로 상대적인 수치를 도출하는 것에서 시작된다.
- RWD에서는 픽셀(Pixel)이 아닌, 상대단위(%, em, rem, vw, vh, vmin, vmax)를 사용해야 하기에 픽셀을 상대 단위로 바꾸는 계산식을 사용해야 한다.
  ```
    Target : context = results
    [font-siex] 24:16 = 1.5em
    [div]       700:988 = 0.7085%
  ```
##### ▷ 테크니컬 이슈
  - 물처럼 흐르는 유연한 레이아웃을 구현할 경우 발생하는 테크니컬 이슈는 웹 브라우저가 퍼센트(%) 값을 픽셀(px) 값으로 변경하는 과정에서 발생.
  - 정확하게 정수로 떨어지지 않는 픽셀의 경우 각 브라우저마다 처리하는 방식이 다르기 때문
  - flex box를 사용하여 문제 해결 가능.

### 유연한 이미지
- 유연한 이미지(Fluid image)는 이미지를 포함하는 컨테이너 요소의 폭에 맞춰 크기가 변경되는 이미지를 말함.
  ```CSS
  .img{
    width:100%; height: auto;
  }
  .background{
    width: 100%;
    padding-bottom:calc(1000/800*100%); /* 실제 이미지 크기 : width:800px / height:1000px */
    background: url(이미지경로) no-repeat center;
    background-size: contain; /* contain , cover ...*/
  }
  ```

### 재단 이미지
- 재단 이미지(Crop Image)는 이미지를 포함하는 컨테이너 요소의 폭에 맞춰 크기가 동적으로 잘려지는 이미지를 말함.
  ```CSS
  :root {
    --bg-image: url("이미지경로");
  }
  .background{
    width:100%;
    height: 960px; /*고정값 설정*/
    background:var(--bg-image) no-repeat center;
    background-size:cover; /* contain , cover ...*/
  }
  ```
  ```CSS
  .container{
    position: relative;
    height: 120px; /*고정값*/
  }
  .img{
    position: absolute;
    top:0; left:50%;
    width:100%;
    height: auto;
    transform: translateX(-50%;);
  }

  ```
### 유연한 미디어
- 유연한 아이프레임(Flexible iframe)은 아이프레임을 포함하는 컨테이너 요소의 폭에 맞춰 크기가 변경되는 것을 말함.
  ```CSS
    /* img, video 요소에 설정 */
    .rwd-image, .rwd-video {
      width: 100%;
      max-width: 100%; /* 비트맵 이미지의 경우 이미지 자체 크기보다 커지지 않게 설정 */
      height: auto;
    }

    /* iframe, embed, object 부모 요소에 설정 */
    .rwd-media {
      overflow: hidden;
      position: relative;
      max-width: 100%;
      height: 0 !important;
    }

    /* 영상 화면 비율에 따른 멀티 클래스 */
    .rwd-media.is-4x3  { padding-top: calc(3/4*100%);  }
    .rwd-media.is-16x9 { padding-top: calc(9/16*100%); }
    .rwd-media.is-21x9 { padding-top: calc(9/21*100%); }

    /* .rwd-media 내부 iframe, embed, object 요소 설정 */
    .rwd-media iframe,
    .rwd-media object,
    .rwd-media embed {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      border: 0;
    }
  ```
</div>
</details>

---------------------------------------

<details>
<summary>17일차 학습</summary>
<div markdown="17">

### 장치 독립적 픽셀

</div>
</details>

---------------------------------------

<details>
<summary>18일차 학습</summary>
<div markdown="18">

### 중단점과 미디어 쿼리

</div>
</details>

---------------------------------------

<details>
<summary>19일차 학습</summary>
<div markdown="19">

## WAI-ARIA(RIA를 위한 접근성 권고안)
### WAI-ARIA 소개
### WAI-ARIA 지원현황
# WAI-ARIA 역할(Role)
### WAI-ARIA 속성(Properties)과 상태(States)
### WAI-ARIA 사용 규칙
### WAI-ARIA 자동완성 UI
### WAI-ARIA 데이터 검증 결과
### WAI-ARIA 레이어 팝업


</div>
</details>

---------------------------------------

<details>
<summary>19일차 학습</summary>
<div markdown="19">

## 웹 콘텐츠 접근성 지침(WCAG)
### 인식 (Perceivable)
### 운용 (Operable)
### 이해 (Understandable)
### 견고 (Robust)

</div>
</details>
