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
  ```
  해당 예시는 CSS에서 새롭게 제공하는 변수 선언 방식을 의미합니다.
  :root라는 가상 클래스를 사용하여 문서 트리의 루트 요소를 선택자로 지정한 후 변수 선언 및 값을 할당합니다.
  이 때 변수 선언은 전역(global)인 :root에서만 가능합니다.
  그 후 원하는 선택자에 변수에 선언한 값을 사용하고자 할 경우 var( )함수를 사용하여 변수를 참조하는 것입니다.
  이렇게 변수를 사용하면 중복된 값을 일일이 지정하지 않아도 된다는 장점이 생기고 값의 수정도 용이해집니다.
  이런 변수 방식은 Sass나 Less 등 CSS 전처리기에서 이미 사용하고 있는 방식이지만 CSS 표준에도 드디어 등장한 것입니다.
  다만 IE는 Edge15이상에서만 사용할 수 있습니다.
  아래 URL을 한번 살펴보시기 바랍니다.
  https://developer.mozilla.org/ko/docs/Web/CSS/:root
  https://developer.mozilla.org/ko/docs/Web/CSS/var
  ```
---------------------------------------

## 반응형 디자인(RWD)
<details>
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
#### ▷ 픽셀 밀도
  - 공간(대부분 inch에서 사용)에 픽셀이 들어가는 물리적인 수치를 말함.
  - 첫 번째 맥킨토시 컴퓨터는 인치당(inch) 72픽셀.

#### ▷ 디바이스 픽셀 밀도
  - 애플사가 2010년 inch당 픽셀을 x2 배로 올려 엄청나게 선명한 레티나 디스플레이를 소개한 이후, 디자인(설계) 과정에서 디바이스 픽셀을 고려해야함.
  - 벡터 그래픽과 달리 비트맵 그래픽은 디바이스 픽셀밀도(Device Pixel Density)에 영향을 받음. 고해상도를 지원하는 디바이스에 적합한 그래픽 제작이 필요.

#### ▷ 디바이스 별 UI 크기
  - 물리적으로 동일한 UI 크기를 유지하려면 픽셀 면적이 x2배일 때, 44px 크기 버튼은 88px이 되어야 함. 각기 다른 디바이스에 이와같은 UI개념을 적용하기 위해 디자이너는 원래x1 크기 제작은 물론 x2 크기 제작이 필요해짐.
  - 수치 측정 단위 중 픽셀 밀도를 측정하는 독립적인 단위가 없어 디자인 제작과정이 곤란스러워짐. 이에 대한 해결책을 애플은 `Point(pt)`를 제시함.
    - 웹 UI와는 별개. 어플리케이션 용도. 인쇄용 규격인 pt와는 다름.
  - 애플과 달리 안드로이드 진영은 장치 독립적인 픽셀 밀도(DIP) 단위인 `DP`를 만들어냄. 문제는 정수 배율을 가진 애플과 달리 실수 배열을 가졌다는 점.
    - 웹 UI와는 별개. 실수 - 애플과 달리 디바이스 크기가 너무 다양하기 때문.

#### ▷ 밀도 변환기
  - 픽셀(px) 값을 입력하면 각 디바이스 밀도에 해당되는 픽셀 값을 반환하는 도구.

#### ▷ 디바이스 픽셀 밀도 UI 그래픽 내보내기
  - 포토샵을 사용하는 그래픽 디자이너는 x1 배율의 벡터 그래픽을 제작한후, 디바이스 픽셀 밀도를 고려하여 내보내야 함.(비트맵의 경우 스마트오브젝트를 사용)

#### ▷ 사람이 보는 크기의 인식 고려
  - Input Method 마우스 포인터보다 손가락의 크기가 큰것을 고려하기
  - Physical Screen Size 물리적 화면크기 고려하기
  - Distance form Scree 사용자와 화면사이의 거리 고려하기 - ex) TV / 컴퓨터 모니터
  - 태블릿에서의 앱 아이콘은 폰보다 크기가 커야함.
  - 해결 방법 2가지
    1. **픽셀 밀도 낮추기**
      - 대형 스크린은 멀리서 보기에 보통 낮은 픽셀 밀도를 가짐.
      - 일반적으로는 TV는 생각보다 아주 낮은 인치당 40px / 아이폰 레티나는 326ppi /  아이패드 레티나는 226ppi
      - 아이패드의 큰 픽셀(스크린은 덜 빽빽함)이 인터페이스를 약간 크게 보이게 해줌.
    2. **크기 바꾸기**
      - 픽셀 밀도를 낮추는 것만으로는 충분하지 않아 특정 디자인 요소들은 큰 크기로 만들어야 하기도 함.
      - 아이패드 앱 아이콘에서 이러한 경우가 발생하는데 아이폰에서는 앱 아이콘이 60x60 크기인데 아이패드의 큰 스크린은 더 큰 공간을 필요로 하기에 76x76 크기의 앱 아이콘을 사용하여 시각적인 크기 개선을 해야함.

#### ▷ 디자인 시작점
  - 사진 같은 비트맵 이미지를 제외하고 대부분의 UI는 벡터를 사용하여 제작.
  - 디자인 배율은 x1에서 시작.
  - 비트맵 이미지는 스마트 오브젝트를 사용하여 내보내기.

</div>
</details>

---------------------------------------

<details open>
<summary>18일차 학습</summary>
<div markdown="18">

### 중단점과 미디어 쿼리
#### ▷ 브레이크 포인트
- RWD 프로젝트 진행 전, 주요 사용자 층이 사용하는 디바이스 환경을 분석한 후, 최적화되고 유효한 중단점(Breakpoint)을 설계(Design) 한다.

#### ▷ CSS3 미디어쿼리
- 미디어 쿼리는 각 디바이스 환경을 식별하는 조건 처리 구문으로 CSS3에서 정식 지원함. 이를 사용하여 설계된 중단점에는 맞는 최적화된 뷰 디자인을 구현할 수 있다.
```
  @media {type} and (expression){ css code }

  - type : screen/printer/tv/integration css rule / projector
  - expression : width/height/color/aspect ratio/resolution/orientation
```
- W3C 표준 미디어쿼리 사양
  | Feature | Value | Min/Max | Description |
  |---|---|---|------|
  |width|length|yes|Display width|
  |height|length|yes|Display height|
  |orientation|portrait or landscape| **no** |Device orientation|
  |aspect-ratio|ratio(w/h)|yes|Ratio of width to height|
  |Device-aspect-ratio|ratio(w/h)|yes|Ratio of device-width to device-height|
  |color|integer|yes|Number of bits per color component|
  |color-index|integer|yes|Number of entries in the output device's color lookup table|
  |monochrome|integer|yes|Number of bits per pixel in the monochrome frame buffer|
  |resolution|resolution|yes|Density of pixel of output device, (integer followed by dpi or dpcm)|

  ```css
    /* width */
    @media screen and (min-width:200px) and (max-width:400px){ }

    /* height */
    @media (min-height:500px) and (max-height:580px){ }

    /* portrait */
    @media screen and (orientation : portrait) { }

    /* landscape */
    @media screen and (orientation : landscape) { }

    /* 300 DPI */
    @media print and (min-resolution : 300dpi) { }

    /* x2 Device Pixel Density */
    @media screen and (min-resolution : 2ddpx) { }

    /* AND */
    @media all and (color) { }
    /* NOT + AND */
    @media not screen and (color) { }  
    /* ONLY + AND */
    @media only screen and (orientation:portrait) { }  
    /* COMMA */
    @media all and (orientation:landscape),
           all adn (min-width:480px) { }  
  ```

#### ▷ 모바일 퍼스트(Mobile First)
- 현 시대 사용자 대부분이 모바일 환경에서 우선 접속.(일상)
- 필요에 따라서는 데스크탑 환경이 필요(업무) 할 수 있으나, 사용자를 고려한 설계 관점에서 사용자 대다수가 우선하는 모바일 환경 디자인(설계)이 우선시 되어야 함.

#### ▷ 중단점 설계
- 서비스를 이용하는 주 고객층의 행동 패턴을 분석하여 모바일, 태블릿, 데스크탑, 와이드 스크린 사용율 통계를 검토한 후,  기기의 속성(스크린 폭, 해상도 등)을 고려하여 중단점을 설계해야 함.
  - 중단점 설계를 위한 참고 자료
    - http://gs.statcounter.com  
    - http://www.w3counter.com/globalstats.php?year=2018&month=3
    - http://www.internettrend.co.kr/trendForward.tsp
    - http://troy.labs.daum.net

  - 고려해야 할 중단점
    - ⇐  (640) / 800  ⟺  (1024) / 1366  ⟺  1920  ⇒
    - ※ 중단점은 최소한으로 설정할 필요가 있다. 중단점이 많아지게 되면 기획/디자인/개발 과정이 모두 고통스러워지기 때문.
  - 고민해야 할 사용자 행동 패턴
    - 1920 스크린 해상도를 사용하는 사용자가 풀 스크린으로 브라우저를 화면 가득 띄워놓고 사용하는지 확인 필요.
    - 그렇지 않다면 1366 기준으로 설계하되, 1920까지 고려하는 방향으로 전략 수립.

  - 예시 : 중단점 및 미디어 쿼리 설계 (사용자 환경, 시대에 따라 변경됨)
    ```css
    /*
    800 ⟺ 1024 ⟺  1600
    50em ⟺ 64em ⟺ 100em
    */
    @media ( min-width: 50em ){}
    @media ( min-width: 64em ){}
    @media ( min-width: 100em ){}
    ```
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
<summary>20일차 학습</summary>
<div markdown="20">

## 웹 콘텐츠 접근성 지침(WCAG)
### 인식 (Perceivable)
### 운용 (Operable)
### 이해 (Understandable)
### 견고 (Robust)

</div>
</details>
