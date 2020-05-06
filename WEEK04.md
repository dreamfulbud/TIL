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

<details open>
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

<details open>
<summary>19일차 학습</summary>
<div markdown="19">

## WAI-ARIA(RIA를 위한 접근성 권고안)
### WAI-ARIA 소개
  #### 웹콘텐츠 접근성 지침
  - WAI(Web Accessibility Initiative)
  - WCAG(Web Content Accessibility Guidelines)
  - 시각 장애인, 저시력자, 청각 장애 및 상지 장애 등 다양 장애를 가진 사람들에게 보다 접근 가능한 콘텐츠를 제공하는 것 목표로 함.
  - 한국형 웹콘텐츠 접근성 지침(KWCAG) 2.1 -  2013.12.18
  - 웹 콘텐츠 접근성 가이드 라인의 버전이 업데이트 되면서 웹접근성 보장 수준이 좋아지고 있으나, 새롭게 등장하는 신기술들을 지원하기에 아직도 부족하다.

#### 웹 콘텐츠 접근성 지침이 기술적, 환경적으로 지원하기 어려운 문제
  - RIA의 동적인 웹 애플리케이션 접근성 보장을 위한 지침이 부족.
  - Ajax를 통한 실시간 변경 콘텐츠를 못 읽을 수 있음.
  - 페이지 콘텐츠 중 일부만 변경 시, 동일한 내용을 계속 읽어야 하는 문제 발생.
  - 화면 확대 사용자의 경우, 가시 범위 밖의 콘텐츠 변경 내용을 알 수 없음.

#### WAI-ARIA 목적
- WAI-ARIA는 스크린리더 및 보조기기 등에 접근성 및 상호 운용성을 향상시키기 위해 마크업에 역할(Role), 속성(Property), 상태(State) 정보 추가할 수 있도록 지원.
- 이렇게 추가된 정보는 웹 브라우저에 의해 자동으로 해석되어 각각의 운영체제(OS)의 접근성 API로 변환되도록 설계.
- 이때 스크린리더 및 보조기기는 운영체제(OS)에서 제공하는 접근성 API를 통해 데스크탑 애플리케이션과 동일한 방법으로 Javascript 컨트롤을 인식하고 상호 작용.
```
 마크업에 역할(Role), 속성(Property), 상태(State) 정보를 추가하여 스크린 리더 및 보조 기기 등에서 접근성 및 상호 운용성을 향상시키고 보다 나은 사용자 경험(UX)을 제공하기 위함
```

#### WAI-ARIA 지원현황
- 모던 웹브라우저의 지원 수준은 상당히 높은 편.
- 스크린리더와 웹브라우저의 조합에서 WAI-ARIA 호환성은 2020.01.11 기준 JAWS-Chrome 이 가장 높은편
https://www.powermapper.com/tests/screen-readers/aria/

#### WAI-ARIA 역할(Role)
- 특정 요소(Element)에 역할을 정의하는 것.
- 역할을 부여하여 사용자에게 정보를 제공.
- 부여된 역할은 **동적으로 변경할 수 없음**.
```html
  <!-- 메뉴 정의 -->
  <div class="user_menu" role="menu"></div>

  <!-- 경고 대화상자 정의 -->
  <div class="auth_error" role="alertdialog"></div>

  <!-- 버튼 정의 -->
  <a class="btn_01" role="button"></a>
```

#### WAI-ARIA 속성(Properties)과 상태(States)
- 요소(Elemnet)가 기본적으로 갖고 있는 특징이나 상황
- 속성과 상태는 `aria-` 접두어를 가진다.
- 상태는 요소의 상황을 나타내므로 애플리케이션이 실행 중에 자주 바뀌는 반면, 속성은 상대적으로 바뀌는 경우가 드물다.
  - 속성(Properties)
    ```html
      <!-- 필수 항목 속성 -->
      <input type="checkbox" aria-required="true">

      <!-- 추가 설명 속성 -->
      <input type="text" aria-describedby="reference">
      <div id="reference">추가설명
        ex) 영어 대소문자 및 특수문자와 숫자 등 3가지 이상의 유형의 조합으로 최소 10글자 이상 입력
      </div>

      <!-- 그룹 레이블 명명 -->
      <div role="group" aria-label="레이블"></div>
    ```
  - 상태(States)
    ```html
      <!-- 확장되어 있는 상태의 탭패널 false:접혀진 상태 -->
      <div role="tabpanel" aria-expanded="true"></div>

      <!-- 오류가 발생한 상태의 입력상자-->
      <input type="text" aria-invalid="true">

      <!-- 선택된 상태의 토글버튼 -->
      <button aria-pressed="true"></button>
    ```

### WAI-ARIA 사용 규칙
- ARIA 역할(role)과 HTML5 섹션 요소를 중복해서 사용하지 않는다.
  ```html
    <!--잘못된 사례-->
    <nav role="navigation"></nav>
  ```
  - ARIA 역할(role)과 HTML5 섹션 관련 요소 비교
    | ARIA role | HTML5 section | 비고 |
    |----|----|----|
    | application | X | 주로 `div` 요소와 같이 그룹 역할을 하는 요소로 대체 |
    | banner | X | 비슷한 의미로 `header` 요소 사용 가능. `<header role="banner">`로 사용하였다면 한 페이지에서 한개의 요소만 사용하길 권장 |
    | navigation | nav | 다른 페이지 또는 페이지 내 특정 영역의 이동으로 이동하는 링크 콘텐츠 영역으로 주로 메인 메뉴 및 서브 메뉴 등에 사용 가능|
    | main | main | 본문의 주요 콘텐츠 영역으로 한 페이지 내에 1개만 사용 가능. `article` `aside` `footer` 요소의 하위 요소로 사용 불가 |
    | aside | aside | 주요 콘텐츠와 연관이 적은 의미있는 콘텐츠 영역으로 종종 사이드바로 표현 가능. `aside` 영역에는 현재 날씨, 관련된 기사 또는 주식 정보 등의 부가 콘텐츠 포함 가능. |
    | form | form | 폼과 관련된 요소의 모임을 표현하는 영역으로 서버에 전송될 수 있는 콘텐츠 포함 가능. |
    | search | X | 검색의 역할을 담당하는 서식 영역임을 의미하며 `div` 또는 `form` 요소를 사용하는 것을 권장. |
    | contentinfo | X | 비슷한 의미로 `footer` 요소를 사용할 수 있으나  `<footer role="contentinfo">`로 사용하였다면 한 페이지에서 한개의 요소만 사용하길 권장 |

- HTML 요소의 기능변경 제한
  ```html
    <!--잘못된 사례-->
    <h1 role="button">버튼</h1>

    <!--올바른 사례-->
    <h1><button>버튼</button></h1>
    <h1><span role="button">버튼</span></h1>
  ```

- 키보드 사용 보장
  - 사용자와 상호작용이 필요한 대화형의 UI의 경우 키보드로도 접근 및 사용이 가능하도 제공.
  - 상호작용이 필요한 대화형의 UI : 사용자가 클릭할 수 있는 정보나 탭 또는 드래그 앤 드롭, 슬라이드, 스크롤 등의 기능이 필요한 콘텐츠를 의미.
  ```html
    <!--잘못된 사례-->
    <span role="button">버튼</span>

    <!--올바른 사례 : 음수값은 포커스 X-->
    <span role="button" tabindex="0">버튼</span>
  ```

- 숨김콘텐츠
  - 사용자에게 정보를 전달하되 단순히 화면에서만 보이지 않도록 처리된 콘텐츠에
    - `aria-hidden="true"`를 지정해서는 안됨 - 의미적으로도 숨겨진 콘텐츠로 인식.
    - `role="presentation"`를 주어서도 안됨 -의미없이 단순히 가시적으로 전달하기 위한 요소로 인식.
    ```html
      <!--잘못된 사례-->
      <button aria-hidden="true">버튼</button>
      <button role="presentation">버튼</button>

      <!--올바른 사례-->
      button{ display:none;}
      <button aria-hidden="true">버튼</button>
    ```

- 레이블 제공
  - 모든 대화형 UI의 경우 반드시 레이블을 제공하여야 함.
  ```HTML
    <div>
      <div id="user-name">이름</div>
      <input type="text" id="name" aria-labelledby="user-name">
    </div>
  ```

- 유효성 검사
  - 의미를 가지는 시맨틱 요소와 충돌되지 않도록 주의.

### WAI-ARIA 자동완성 UI
- [도서검색]
- before : 기존의 자동완성 기능은 편집창에서 목록이 펼쳐질 때, 화면낭독기를 통한 안내를 제공하지 않아 시각장애인 사용자는 자동완성 기능의 존재를 인식하지 못함.
- after : aria-live를 활용하여 자동완성 목록의 수를 제공하면, 시각장애가 있더라도 화면낭독기를 통해 자동완성 기능의 동작을 명확하게 인식할 수 있다.

#### aria-live
- 페이지 중 어떤 부분을 '라이브'로 표시 가능. 페이지의 어느 위치에 있든 상관없이 새롭게 업데이트된 정보를 사용자에게 즉시 알릴 수 있음.
- ex)사용자 작업의 결과로서 나타나는 상태 메시지

```HTML
  <div class="status" aria-live="polite">Your message has been sent.</div>
```
- 속성값 -  polite, assertive, off
  - `polite`
    - 보조 기술이 현재 어떤 작업을 하고 있든 그 작업을 마치면 보조 기술 사용자에게 이런 변경 사항을 알리도록 하는 역할
    - 중요하지만 긴급하지는 않은 변경 사항일 경우에 적합하며 aria-live는 대부분의 이런 용도로 사용됩니다.
  - `assertive`
    - 보조 기술이 수행 중인 작업이 무엇이든 중단하고 사용자에게 이런 변경 사항을 즉시 알리도록 하는 역할.
    - '서버 오류가 발생하여 변경 내용이 저장되지 않습니다. 페이지를 새로 고치세요' 같은 상태 메시지나 스테퍼 위젯에 있는 버튼처럼 사용자 작업의 직접적 결과로서 입력란이 업데이트되는 경우와 같이 중요하고도 긴급한 업데이트에만 이 값을 사용.
  - `off`
    - 보조 기술이 aria-live 인터럽트를 일시적으로 중단하도록 하는 역할

- 올바로 작동하도록 하기 위한 방법
  1. 처음에 페이지를 로드할 때 aria-live 영역을 설정
  2. 각 스크린 리더는 다양한 유형의 변화에 각기 다르게 반응.
    - ex) 하위 요소의 hidden 스타일을 true에서 false로 전환해 스크린 리더에서 경고를 발생시킬 수 있음.

[참고] https://developers.google.com/web/fundamentals/accessibility/semantics-aria/hiding-and-updating-content?hl=ko

### WAI-ARIA 데이터 검증 결과
- [회원가입 아이디 비밀번호]
- before : 화면낭독 프로그램으로 웹에서 실시간으로 갱신되는 정보를 인식하는 것은 매우 어렵다. 동적으로 변경되는 기존의 데이터 검증결과는 화면낭독프로그램에서 음성출력되지 않아 시각장애인 사용자가 결과를 인식할 수 없다.
- after : aria-live를 사용하면 실시간으로 갱신되는 정보가 화면낭독 프로그램에서 음성 출력되어 시각장애인 사용자가 정보를 명확하게 인식할 수 있다.

### WAI-ARIA 레이어 팝업
- before : 기존에 레이어팝업을 제공하던 방식은 마크업이 연속적이지 않아 레이어팝업 영역에 접근하기 어렵다. 또한 레이어팝업 영역 외에 딤드된 영역도 모두 접근되어 화면낭독기 사용자가 혼란을 느끼게 된다.
- after : 레이어팝업 영역에 `role="dialog"`를 사용하면 마크업이 연속적이지 않아도 바로 접근할 수 있다. 또한 레이어팝업 영역 외에 다른 영역은 화면낭독기에서 접근되지 않기 때문에 콘텐츠를 명확히 인식할 수 있다.


[더 자세한 공부] https://www.youtube.com/channel/UCTI6h7Vb05Td63qHQ3wjySQ/featured

</div>
</details>

------------------------------------

<details open>
<summary>20일차 학습</summary>
<div markdown="20">

## 웹 콘텐츠 접근성 지침(WCAG)
#### 모두를 고려한 디자인
- 모든 상황과 모든 사람을 고려. 가능한 많은 사람들이 우리의 서비스를 이용할 수 있도록 만들어야 함.
- 모든 상황과 사용자를 포함하도록 설계 함으로써 모든 사람의 경험을 개선할 수 있음.
- 실제로 장애가 없는 사람들의 60%는 접근성 기능을 사용. 장애(Disability)는 개개인의 건강 상태에 따라 달라 지는 것이 아니라, 사람과 인터랙션(상호작용) 할 수 없음을 말하는 것.
- 접근성을 향상시키면 사용성은 자연스레 향상됨.

#### 쉽고 단순한 것이 최고의 디자인
- 쉬운 말 사용
- 명확한 대비 사용 - 전경과 배경색의 대비 4.5:1
- 이미지 설명 - `alt`
- 키보드 사용자 고려
- 클릭 영역을 크게 만들기 - 장애를 가진 사용자뿐만아니라 터치스크린을 사용하는 사용자에게도 도움됨.
- 논리적으로 구성 - 중요한 콘텐츠, 중요한 정보를 놓치지 않도록.
- 사용자 테스트.

## 웹 콘텐츠 접근성 가이드라인
### WCAG란?
- W3C 웹 콘텐츠 접근성 가이드라인 표준 권고안은 웹 사이트/애플리케이션에서 충족해야 하는 기준을 정의하여 장애가 있는 사용자가 보다 쉽게 이용할 수 있도록 준수해야 하는 지침.
- 웹 서비스를 제작하는 사람들이 기획/디자인/개발 과정에서 고려해야 할 요구사
- 접근성은 시각 (Visual) / 청각 (Auditory) / 지체 (Physical) / 음성 (Speech) / 인지 (Cognitive) / 언어 (Language) / 학습 (Learning) / 신경 (Neurological) 장애를 포함한 광범위한 장애를 포함.


### 1. 인식 (Perceivable)
- 모든 사용자는 서비스 콘텐츠를 인식할 수 있어야 합니다.

#### 1.1 대체 텍스트
- 텍스트가 아닌 콘텐츠에 대한 적절한 텍스트를 제공해야함.

  ##### 1.1.1 텍스트가 아닌 콘텐츠 (A)
  1. 컨트롤,입력
  2. 시간 기반 미디어 - 대체수단 제공(자막,원고,수화)
  3. 테스트
  4. 감각 - 예술품과 같은 것에 대한 묘사는 명확하고 간결하게 기술.
  5. 보안 문자 - 음성 CAPCHA 제공
  6. 장식성, 포멧팅, 안보이는

***
#### 1.2 시간 기반 미디어
- 시간 기반 미디어의 대체수단을 제공해야함.

  ##### 1.2.1 오디오, 비디오 (A)
  ##### 1.2.2 캡션 (A)
  ##### 1.2.3 오디오 설명, 미디어 대체물 (A)
  ##### 1.2.4 라이브 캡션 (AA)
  ##### 1.2.5 오디오 설명 (AA)
  ##### 1.2.6 수화 (AAA)
  ##### 1.2.7 확장 오디오 설명 (AAA)
  ##### 1.2.8 미디어 대체물 (AAA)
  ##### 1.2.9 라이브 오디오 (AAA)

***
#### 1.3 적응성
- 정보 구조를 잃지 않고 다양한 방식(예: 간단한 레이아웃)으로 표현할 수 있는 컨텐츠를 만듦.

  ##### 1.3.1 정보 및 관계 (A)
  - 표현을 통해 정보, 구조 및 관계는 프로그래밍 방식으로 결정되거나 텍스트로 제공.

  ##### 1.3.2 의미적인 순서 (A)
  - 콘텐츠가 제시되는 순서가 의미에 영향을 줄때, 올바른 판독 순서가 프로그래밍 방식으로 결정될 수 있음.

  ##### 1.3.3 감각적 특성 (A)
  - 콘텐츠를 이해하고 조작하기 위해 제공된 가이드라인은 **모양, 색, 크기, 시각적 위치, 방향 또는 소리** 와 같은 컴포넌트의 감각적인 특성에만 의존하지 않는다.

  ##### 1.3.4 기기 회전 (AA)
  - 특정 디스플레이 방향이 필수적이지 않는 한, 콘텐츠는 보기 및 작동을 세로 또는 가로. **한 방향으로 제한 하지 않음.**
    ```
    이 지침을 준수하면 태블릿, 스마트폰 등을 휠체어에 장착하거나,
    운동 능력이 제한되어 있거나, 현재 손이 바쁘기 때문에
    휠체어를 돌리는데 어려움이 있는 사용자의 접근성이 개선 될 것.
    모든 방향에서 애플리 케이션을 사용할 수 있도록 만들면 누구나 혜택을 얻을 수 있음.
    ```
    - 예외) 은행 체크(수표 스캔 인식), 피아노 애플리케이션, 프로젝터 또는 TV용 슬라이드, 바이너리 디스플레이 방향이 적용되지 않는 가상 현실(VR) 컨텐츠

  ##### 1.3.5 입력 목적 식별 (AA)
  - 사용자의 관한 정보를 수집하는 각 입력 필드의 목적은 프로그래밍 방식으로 결정.
  - 이 지침을 준수하면 인지 장애가 있는 사용자가 텍스트를 읽고 입력하는 것이 쉬워져 접근성을 향상시킴. 또한 웹 사이트의 언어를 잘 모르는 사용자 또한 접근성이 향상됨.
    - 입력필드는 UI 컴포넌트의 입력 용도 섹션에서 식별된 용도록 사용
    - 콘텐츠는 폼 입력 데이터에 대해 예상되는 의미를 식별 할 수 있는 기술을 사용하여 구현.
    ```
     메타 데이터를 첨부함으로써 사용자가 입력을 더 잘할 수 있도록 도움.
     이름 및 이메일 주소와 같은 입력을 자동 완성할 수 있도록 구성할 수 있음.
     자동 완성은 브라우저가 이전 입력에서 저장한 정보와 양식 필드에서
     자동 완성을 허용하는 브라우저 기능의 조합으로 작동.
    ```
    - `autocomplete`
      - `email` : 이메일 주소 / `current-password` : 사용자 이름 필드에 의해 식별된 계정의 현재 암호   

      ```HTML
        <form action="/sign-in" method="POST">
          <p class="form-control">
            <label for="input-email">이메일</label>
            <input type="email" id="input-email" autocomplete="email">
          </p>
          <p class="form-control">
            <label for="input-password">비밀번호</label>
            <input type="password" id="input-password" autocomplete="current-password">
          </p>
          <button type="submit">로그인</button>
        </form>
      ```

  ##### 1.3.6 목적 식별 (AAA)
  - HTML 마크업 언어를 사용하여 구현된 콘텐츠에서 UI 컴포넌트, 아이콘 및 영역의 목적을 프로그래밍 방식으로 결정 가능.
  - 이 지침을 준수하면 스크린리더와 같은 보조기술 사용자의 접근성 향상.
    - 의미를 가진 아이콘 콘텐츠의 경우, 사용자에게 이상하게 읽히지 않도록 적절한 대체 텍스트 제공
    - 사용자가 쉽게 탐색할 수 있도록 헤더, 내비게이션, 메인 콘텐츠 영역을 명확히 구분할 수 있도록 함.
    - 사용자가 원하는 콘텐츠를 빨리 찾을 수 있도록 `h2`, `h3`, `h4`와 같은 소제목을 활용
    - ex) `aira-lable` 속성을 사용해 X버튼이 아닌, '닫기 버튼'으로 읽히도록 만들어 버튼의 용도를 보다 쉽게 인식할 수 있도록 구조화.
    ``` HTML
      <button type="button" class="button close-modal" aria-label="닫기">X</button>      
    ```
      | 영역 | 랜드마크 역할 |
      | --------- | --------- |
      | 헤더 | role="banner" |
      | 내비게이션 | role="navigation" |
      | 메인 | role="main" |
      | 보조 | role="complementary" |
      | 푸터 | role="contentinfo" |
      | 섹션 | role="region" |
      | 폼 | role="form" |
      | 검색 | role="search" |

***
#### 1.4 명료성
- 사용자가 콘텐츠를 보고 들을 수 있도록 명확하게 구분.

  ##### 1.4.1 컬러 활용 (A)
  - 색상만으로 정보 전달, 행동을 지시, 반응을 유발, 시각적 요소를 식별하는 시각적인 용도로 사용X

  ##### 1.4.2 오디오 컨트롤 (A)
  - 3초 이상 자동으로 웹페이지가 오디오를 출력한다면, 오디오 재생을 일시정지 하거나 멈추게하는 기능 또는 오디오 볼륨을 조절할 수 있는 기능을 제공

  ##### 1.4.3 대비 (AA)
  - 텍스트 또는 이미지 텍스트의 시각적인 표현은 다음 예외 사황을 제외하고 명도 대비 차는 최소 4.5:1
    - **큰 텍스트** : 24px 이상 또는 18px Bold 텍스트의 경우 3:1 명도 대비 차까지 허용
    - **중요하지 않은** : 비 활성화된 UI컴포넌트 텍스트나 이미지의 텍스트, 순수한 표현 장식, 보이지 않는 콘텐츠, 중요한 다른 시각적인 콘텐츠를 포함하는 그림은 별도의 명도 대비 요구가 없음.
    - **로고타입** : 로고나 브랜드의 텍스트는 최소한의 명도 대비 요구가 없음.

  ##### 1.4.4 텍스트 크기 조정 (AA)
  - 캡션 및 이미지 텍스트를 제외하고, 텍스트는 콘텐츠와 기능의 손실없이 200% 이상 보조 기술 없이 크기 조정이 가능해야 함.

  ##### 1.4.5 이미지 텍스트 (AA)
  - 시각적인 표현을 성취할 수 잇는 기술들이 사용될 때, 텍스트는 다음을 제외하고 이미지의 텍스트 보다 많은 정보를 전달할 수 있어야함.

    - **맞춤 설정 가능** : 이미지 텍스트는 사용자의 요구에 따라 시각적으로 사용자가 조정 가능해야함.
    - **필수** : 텍스트의 특정한 표현은 정보가 전달될 때 필수

  ##### 1.4.6 향상된 대비 (AAA)
  - 텍스트 또는 이미지의 텍스트의 시각적인 표현은 다음 예외사항을 제외하고 명도 대비 차는 적어도 7:1이 되어야 함.(예외사항은 3번 대비와 동일)

  ##### 1.4.7 작거나, 배경음악 아님 (AAA)
  - 일반 오디오(예: 사용자가 의도를 가지고 재생한 음성)이거나, 오디오 CAPCHA 또는 로고송이 아니고, 노래 또는 랩과 같이 가사를 제공하는 음악 표현이 아닌, 사전 녹음된 오디오 전용 콘텐츠의 경우 배경음악이 아님.

    - **배경음악이 아님** : 배경음악을 포함하지 않는 오디오
    - **오디오 끄기** : 배경음악을 끌수 있음.
    - **20데시벨(dB)** : 배경음악의 데시벨 강도가 20dB보다 작음.

  ##### 1.4.8 시각적 표현 (AAA)
  - 텍스트 블록을 시각적으로 표현하기 위해 다음과 같은 매커니즘알 사용가능.
    1. 전경색과 배경색은 사용자가 선택할 수 있어야 함.
    2. 너비는 80글자나 글리프(CJK의 경우 40자)를 넘으면 안됨.
    3. 텍스트는 양쪽정렬이 아니어야 함.(왼쪽과 오른쪽 여백에 양 정렬 됨)
    4. 행간(단란 사이 간격)은 적어도 글자 높이의 1.5배 이상 되어야 함.
    5. 전체화면에서 콘텐츠를 읽거나, 기능을 사용하는데 문제가 없도록, 보조기술 없이 200% 확대하더라도 가로방향으로 스크롤이 생기면 안됨.

  ##### 1.4.9 이미지 텍스트: 예외 X (AAA)
  - 이미지 텍스트는 순수 장식용 또는 텍스트의 특정 표현이 전달되는 정보에 필수 적인 경우에만 사용.
  - 로고타입은 필수적인것으로 간주.

  ##### 1.4.10 리플로우 (AA)
  - 콘텐츠 정보나 기능의 손실없이 양 방향으로 스크롤하지 않도록 제공되어야 함.(CSS픽셀 기준)
    - `320px`에 해당하는 너비의 수직 스크롤링 콘텐츠
    - `256px`에 해당하는 높이의 수평 스크롤링 콘텐츠   

    ```
     웹 사이트를 400%로 확대했을때 가로, 세로 양쪽 방향으로 스크롤바가 생기면 안됨.
     스크롤 바는 가로 또는 세로 방향 한쪽으로만 표시되어야 함.
    ```
    - 400% 확대된 뷰포트 내 콘텐츠가 모두 보여져야 함.
    - 반응형 또는 가변 폭을 활용하여 디자인 함.

  ##### 1.4.11 비 텍스트 명도대비 (AA)
  - 다음의 시각적 표현은 인접한 색상 대비 명도 대비가 최소 3:1 이상 되어야 함.
    - **UI 컴포넌트**
      - 비활성 컴포넌트 또는 컴포넌트 모양이 사용자 에이전트(예:브라우저 등)에 의해 결정되고 개발자에 의해 수정되지 않는 경우를 제외하고, UI 컴포넌트 및 상태를 확인하기 위해 요구되는 시각적 정보
    - **그래픽 객체**
      - 특정 그래픽 표현이 전달되는 정보에 필수적인 경우를 제외하고 콘텐츠를 이해하는데 필요한 그래픽의 일부
  - 링크 텍스트
    - 링크 텍스트가 활성화 된 상태(:hover, :focus, :active 등)를 시각적으로 명확하게 구분할 수 있도록 만들어야 함.
  - 버튼
    - 배경색과 버튼 외곽선 또한 대비 요구 사항을 충족해야함.
  - 입력
    - 텍스트를 입력하는 컴포넌트 또한 활성화 될 경우, 시각적으로 명확하게 구분할 수 있도록 구성.
  - 그래픽 객체
    - 원형 차트 : 각 조각은 인접한 조각색 또는 배경색과 충분한 대비가 있어야 함.
    - 색상만으로 구분하기보다는 형태를 구분할 수 있도록 구성.
    - 각 조각을 당기거나 밀어 각 조각을 쉽게 구분할 수 있게 만들기 / 각 조각의 테두리를 그려 주변 조각과 구분학.
  - 아이콘/인포그래피
    - 아이콘/인포그래피 또한 대비 성공기준에 충족해야함.

  ##### 1.4.12 텍스트 간격 (AA)
  - 행간(줄 사이 간격)은 글자 크기(높이)의 1.5배 이상
  - 단락 간 간격은 글자 크기의 2배 이상으로 간격(마진)을 두어야 함
  - 자간(글자 사이 간격)을 글자 크기의 0.12배 이상
  - 어간(단어 사이 간격)은 글자 크기의 0.16배 이상
  ```
  예외)
  PDF / 이미지 텍스트, 로고, 비디오 캡션(자막) / Canvas 요소를 사용해 구현된 텍스트(이미지 텍스트로 분류)
  ```
  - 텍스트 고정높이 사용X

  ##### 1.4.13 콘텐츠 포커스/호버 (AA)

  - **닫을 수 있는 (Dismissable)**
    - 추가 콘텐츠(예: 툴팁)가 입력 오류를 전달하거나 다른 콘텐츠를 가리거나 교체하지 않는 한, 포인터 호버나 키보드 포커스를 이동하지 않고도 추가 콘텐츠를 닫을 수 있는 메커니즘을 제공.

  - **호버 가능한 (Hoverable)**
    - 포인터 호버로 인해 추가 콘텐츠가 화면에 표시된 경우, 추가 콘텐츠 위로 포인터를 이동해도 추가 콘텐츠는 지속적으로 표시.

  - **지속성 있는 (Persistent)**
    - 추가 콘텐츠는 포인터 호버 또는 포커스 트리거를 제거하거나 사용자가 닫고자 하는 경우가 아니라면, 해당 정보는 지속적으로 화면에 표시.
  ```
  예외)
  사용자 에이전트에 의해 제어되는 추가 콘텐츠의 시각적 표시(예: HTML title 툴팁)는 해당 기준에 부합하지 않dma.
  ```
  - 마우스를 움직이거나, 포커스 활성화 상태에서 콘텐츠를 닫을 수 있어야 함. (예: esc 키를 누르면 닫힌다)
  - 마우스 포인터가 활성화 요소 또는 화면에 표시된 콘텐츠 위에 있을 경우 지속적으로 표시.

---
### 2. 운용 (Operable)
- 모든 사용자는 서비스의 기능을 운용할 수 있어야 합니다.
- UI 컴포넌트와 내비게이션이 작동하는데 문제가 없어야 합니다.

#### 2.1 키보드 접근
- 키보드로 모든 기능을 사용할 수 있어야 함.

  ##### 2.1.1 키보드 (A)
      - 콘텐츠의 모든 기능은 사용자 이동 경로에 따라 달라지는 입력을 요구하는 경우를 제외하고 개별 키 입력에 대한 특정한 타이밍을 요구하지 않는 키보드 인터페이스를 통해 작동할 수 있어야 함.
      - 키보드 조작으로 인해 마우스 입력 또는 기타 입력 방법 사용에 제한이 있어서는 안됨.

  ##### 2.1.2 키보드 함정 X (A)

  ##### 2.1.3 키보드: 예외 X (AAA)
  - 콘텐츠의 모든 기능은 개별 키 입력에 대한 특정 타이밍을 요구하지 않고 키보드 인터페이스를 통해 작동 가능함.

  ##### 2.1.4 문자 키 단축키 (A)
  - 문자 키 단축 키 : 키보드 단축키가 문자(대소문자 포함), 구두점, 숫자 또는 기호 문자만 사용하여 콘텐츠에 구현된 경우 다음 중 하나 이상이 요구 됨.
    - 단축키 기능 끄기 : 단축키를 끌 수 잇는 기능을 제공해야 함.
    - 단축키 재설정 : 1개 이상 프린트 할 수 없는 키보든 문자를 사용하도록 단축키를 다시 매핑 할 수 있는 기능을 제공해야 함.
    - 포커스 상태에서만 활성화 : UI 컴포넌트 단축키는 해당 컴포넌트에 포커스가 있을 때만 활성화.
    ```
      손떨림, 휴대성 또는 인공적인 손을 가진 사람들은
      음성 키보드나 키보드 또는 화면 키보드가 있는 다른 포인팅 장치를 사용하기 때문에
      단일 문자 단축키를 제공할 경우 실수로 문자 단축키를 눌러 원인도 모른채 혼란에 빠질 수 있음.
    ```

***
#### 2.2 충분한 시간 제공
- 콘텐츠를 읽고 사용할 수 있는 충분한 시간을 제공해야함.

  ##### 2.2.1 시간 조절 (A)
  - 콘텐츠에 의해 설정된 시간 제한에 대해 다음 중 하나 이상이 요구 됨.

    - 시간 제한 해제
    - 시간 제한 조정
    - 시간 제한 연장
    - 실시간 예외 : 제한 시간은 실시간 이벤트의 필수로 시간 제한에 대한 대안을 제공하지 않음.
    - 필수 예외 : 시간 제한은 필수적이며 이를 연장하면 활동이 무효화 됨.
    - 20시간 예외 : 제한시간은 20시간을 초과합니다.

  ##### 2.2.2 일시정지, 중지, 감추기 (A)
  - **이동, 깜박임, 스크롤링** : 자동으로 시작하고, 5초이상 지속되며, 다른 콘텐츠와 동시에 표시되는 이동, 깜박임 또는 스크롤 정보의 경우 일시정지, 중지 또는 감추기 기능이 요구됨.
  - **자동 업데이트** : 자동으로 시작하고, 다른 콘텐츠와 병행하여 표시되는 자동 업테이트 정보의 경우 사용자가 일시정지, 중지, 감추기 또는 자동 업데이트를 하지 않는 한 업데이트 빈도를 제어할 수 있는 기능이 요구됨.

  ##### 2.2.3 No 타이밍 (AAA)
  - 타이밍은 인터랙션이 없는 동기화 미디어와 실시간 이벤트를 제외하고, 콘텐츠에 의해 제공되는 이벤트 또는 액션의 필수적인 부분이 아님.

  ##### 2.2.4 중단 (AAA)
  - 긴급 상황과 관련된 중단을 제외하고는 사용자가 중단 또는 연기할 수 있음.

  ##### 2.2.5 재 인증 (AAA)
  - 인증된 세션이 만료 되면, 사용자는 재 인증 후 데이터 손실 없는 행동을 지속 할 수 있어야 함.

  ##### 2.2.6 타임 아웃 (AAA)
  - 사용자가 아무런 행동을 취하지 않고 있을 때, 데이터를 20시간 이상 보존할 수 없는 서비스 공급자는 사용자에게 데이터를 손실할 수 있는 시간 제한에 대해 경고해야함.

***
#### 2.3 발작 예방
- 발작이나 신체적 반응을 일으키는 것으로 알려진 방식으로 콘텐츠를 제작하지 말아야 함.

  ##### 2.3.1 발작 요인 (A)
  - 웹 페이지는 **1초 동안 3번 이상** 깜박이거나, 플래시가 일반 플래시 및 레드 플래시 임계 값보다 낮은 어떤것을 포함해서는 안됨.

  ##### 2.3.2 1초에 3회 이상 깜빡임 (AAA)
  - 1초에 3회 이상 깜빡임 X

  ##### 2.3.3 인터랙션 애니메이션 (AAA)
  - 사용자에게 전달되는 정보에 애니메이션이 꼭 필요하지 않을 경우, 인터랙션에 의해 실행되는 모션 애니메이션을 사용자가 끌수 있도록 만들어 주어야 함.

***
#### 2.4 탐색 가능
- 탐색하고, 콘텐츠를 찾고, 어디에 있는지 판단 할 수 있는 방법을 제공해야 함.

  ##### 2.4.1 블록 우회 (A)
  - 여러 웹 페이지에서 반복되는 콘텐츠 플록을 건너 뛸 수 잇는 기능을 제공해야 함.

  ##### 2.4.2 페이지 제목 (A)
  - 웹 페이지는 주제나 목적을 설명하는 적절한 제목이 제공되어야 함.

  ##### 2.4.3 포커스 순서 (A)
  - 웹 페이지를 순차적으로 탐색할 수 있고 탐색 순서가 의미 또는 작업에 영향을 주는 경우, 포커스 가능 컴포넌트는 의미와 작동 가능성을 유지하는 순서로 포커스를 받아야 함.

  ##### 2.4.4 링크 목적: 컨스트 내 (A)
  - 각 링크의 목적은 링크 텍스트 만으로 또는 링크 텍스트와 프로그래밍 방식으로 결정된 링크 컨텍스트와 함께 결정될 수 있어야 함.(링크의 목적이 일반적인 사용자에게 모호할 경우를 제외)

  ##### 2.4.5 다양한 방법 (AA)
  - 웹 페이지가 프로세스의 결과 또는 단계인 경우를 제외하고 웹 페이지 집합 내에서 웹 페이지를 찾을 수 있는 방법은 여러가지 방법으로 제공 되어야 함.

  ##### 2.4.6 제목과 레이블 (AA)
  - 제목, 레이블은 적절한 주제 및 목적을 설명해야 함.

  ##### 2.4.7 포커스의 시각적 표시 (AA)
  - 키보드로 조작 가능한 UI는 키보드 포커스 상태가 화면에 표시되어야 함.

  ##### 2.4.8 로케이션 (AAA)
  - 일련의 웹 페이지에서 사용자 위치에 대한 정보를 이용 가능하게 해야 함.

  ##### 2.4.9 링크 목적: 오직 링크만 (AAA)
  - 링크의 목적이 일반적인 사용자에게 모호한 경우를 제외하고 링크 텍스트만으로 각 링크의 목적을 식별할 수 있는 방법을 제공해야 함.

  ##### 2.4.10 섹션 제목 (AAA)
  - 섹션 제목은 콘텐츠를 구성하는데 사용.

***
#### 2.5 입력 양식​
- 키보드가 아닌 다양한 입력을 통해 기능을 보다 쉽게 조작할 수 있도록 만들어야 함.

  ##### 2.5.1. 포인터 제스처
  - 멀티 포인트 또는 패스 기반 제스처를 사용하는 모든 기능은 멀티 포인트 또는 패스 기반 제스처가 필수적인 경우가 아니면 패스 기반 제스처 없이 싱글 포인터로 작동할 수 있어야함.

  ##### 2.5.2. 포인터 취소
  - 싱글 포인터를 사용하여 작동할 수 있는 기능의 경우 다음 중 하나 이상이 충족되어야 함.
    - **down 이벤트 사용 X (No Down-Event)**
      - 포인터의 down 이벤트는 함수 일부를 실행하는데 사용하지 않음.
    - **중단(Abort) 또는 실행 취소(Undo)**
      - 함수의 완료는 up 이벤트에 있고 완료 전에 함수를 중단하거나, 완료 후 함수를 실행 취소하는 방법을 제공.
    - **up 이벤트를 통한 취소(Reversal)**
      - up 이벤트는 이전 down 이벤트의 결과를 뒤집을 수 있음.
    - **필수(Essential)적인 상황은 예외**
      - down 이벤트에서 필수적으로 작동해야 하는 경우는 예외입니다.(피아노, 두더지게임)
    ```
    이 지침은 실수로 잘못된 위치를 만지거나 클릭할 수 있는 손떨림, 운동 장애가 있는 사람들을 도움.
    실수로 인해 의도하지 않은 동작이 발생했을 때 취소할 수 있는 기능 제공.
    인지장애가 있는 사람들에게도 도움이 됨. 우연히 컨트롤을 활성화 했기 때문에 예기치 않은 일이 발생하면 혼란스러워질 수 있기 때문.
    뿐만 아니라 일반 사용자 또한 실행 취소 기능을 추가하면 도움이 됨.
    ```
    <!-- (!)공부 필요 -->

  ##### 2.5.3 레이블과 접근 가능한 이름 (A)
  - 텍스트 또는 이미지 텍스트를 포함하는 레이블이 있는 UI 컴포넌트의 경우, 이름에 시각적으로 표시되는 텍스트가 포함되어야 함.
  - 가장좋은 방법은 레이블 텍스트를 이름의 시작 부분에 두는 것.
    - **레이블** : 컨트롤을 식별하기 위한 이름으로 일반적으로 화면에 표시되는 텍스트.
    - **접근가능한 이름(name)** : 보조 기술이 사용자가 컨트롤을 식별하는데 사용되는 이름. **HTML 입력요소의 name 속성과 관련 없음.**
      - 화면에 표시되는 레이블과 접근 가능한 이름을 동일하게 만들어야 함. 이를 수행할 수 없는 경우라면 접근 가능한 이름이 화면에 버튼과 함께 표시되어 사용자로 하여금 접근 가능한 이름을 올바르게 유추할 수 있게 해주어야 함.

  ##### 2.5.4 동작(모션) 실행 (A)
  - 기기 동작이나, 사용자 동작으로 작동할 수 있는 기능은 UI 컴포넌트에 의해 작동할 수 있으며 다음과 같은 경우를 제외하고 우발적인 동작을 방지하기 위해 동작에 대한 응답을 비활성화할 수 있음.
    - **접근성 지원 인터페이스**
      - 모션(동작)은 접근성 지원 인터페이스를 통해 기능을 조작하는데 사용.
    - **필수 상황**
      - 모션 기능이 필수적인 경우는 예외로 함.
  - 필수적으로 동작(모션)이 작동을 위해 필요한 경우가 아니라면 동작에 의존하지 않는 것이 좋으나, 동작을 통한 기능 수행이 필요한 경우 대체 인터페이스를 제공하고, 해당 기능을 끌 수 있도록 해야 함.

  ##### 2.5.5 실행 영역 (AAA)
  - 포인터 또는 터치에 의한 실행 영역은 다음 경우를 제외하고는 44x44 CSS 픽셀 이상(모바일 9mm).
    - **동등한 기능 존재**
      - 동일한 페이지에서 실행 영역이 44x44 CSS 픽셀 이상인 동일한 링크 또는 컨트롤이 존재하는 경우
    - **인라인**
      - 실행 영역이 문장 또는 문장 블록인 경우
    - **사용자 에이전트 컨트롤**
      - 실행 영역이 개발자가 작성한 마크업이 아닌, 사용자 에이전트(예:브라우저)에 의해 결정되는 경우
    - **필수**
      - 실행 영역을 시각적으로 표시하는 것이 정보 전달에 필수적일때
    ```
     컨트롤을 정확히 터치 하기 힘든 사람들에게 도움되는 지침.
     마우스 스틱과 같은 대체 포인터를 사용하는 사람들 또는
     손가락이 마우스 포인터 만큼 정확하지 않은 사람들을 말함.
    ```
  - `<button>`, `<select>`, `<input type="radio">`와 요소와 같은 표준 HTML 컨트롤은 개발자가 임의로 스타일을 조정하지 않을 경우 이 성공기준에서 예외 처리

  ##### 2.5.6 동시 입력 메커니즘 (AAA)
  - 웹 콘텐츠는 제한이 필수적인 경우, 예를 들면 콘텐츠 보안 보장 또는 사용자 설정을 침해하면 안되는 경우를 제외하고 플랫폼에서 사용할 수 잇는 입력방식을 제한하지 않음.
  - 개발자는 사용자가 터치 또는 마우스만 사용한다고 가정하여 개발 해서는 안됨. 사용자가 입력하는 다양한 방식을 고려하고 연구하여 개발
---
### 3. 이해 (Understandable)
- 모든 사용자가 서비스의 콘텐츠, 기능 사용법 등을 이해하기 쉬워야 합니다.

#### 3.1 가독성
- 텍스트 내용을 읽고 이해하기 쉽게 작성.

  ##### 3.1.1 기본 언어 설정 (A)
  - `<html lang="ko-KR">`

  ##### 3.1.2 보조 언어 설정 (AA)
  -  `<p lang="en-US">`

  ##### 3.1.3 익숙하지 않은 단어들 (AAA)
  - 숙어 또는 전문용어 등 확인하는 기능 제공

  ##### 3.1.4 약어 (AAA)
  - `<abbr title="설명">`

  ##### 3.1.5 읽기 수준 (AAA)
  - 복잡한 내용 - 사용자의 이해를 돕기위해 보조 설명, 적절한 이름, 제목 등을 제공

  ##### 3.1.6 발음 (AAA)
  - 문맥 상에서 알려진 발음없이 모호한 단어의 의미가 있는 단어들의 특정한 발음을 알기 쉽게 하는 기능 제공

***
#### 3.2 예측 가능성
- 예측 가능한 범주 내에서 작동 할 수 있도록 만들어야 함.

  ##### 3.2.1 포커스 상태 (A)
  - 포커스 상태가 되면, 컨텍스트를 변경하지 않음 **ex)슬라이딩 배너**

  ##### 3.2.2 입력 상태 (A)
  - UI 컴포넌트 설정을 변경해도 컴포넌트를 사용하기 전에 사용자에게 동작을 알리지 않는 한, 자동으로 컨텍스트가 변경되어서는 안됨. **ex)패밀리사이트로 이동 - select 선택 후 바로 페이지 이동X**

  ##### 3.2.3 일관된 네비게이션 (AA)
  - 웹 페이지의 집합 내의 여러 웹 페이지에서 반복되는 내비게이션은 사용자가 변경을 시작하지 않는 한, 반복할 때마다 상대적으로 동일한 순서로 발생해야함.

  ##### 3.2.4 일관성 (AA)
  - 웹 페이지 집합 내에서 동일한 기능을 가진 컴포넌트는 일관되게 구별되어야 함.

  ##### 3.2.5 요구 변경 (AAA)
  - 컨텍스트 변경은 사용자 요청에 의해서만 시작되거나, 변경 사항을 끄는 기능을 제공 **ex)영상 자동 재생X**

***
#### 3.3 입력 도움
- 실수를 피하고 해결할 수 있도록 도움을 제공

  ##### 3.3.1 오류 확인 (A)
  - 입력 오류가 자동으로 감지되면 오류가 잇는 항목이 확인되고 오류를 텍스트로 사용자에게 설명

  ##### 3.3.2 레이블 또는 지침 (A)
  - 콘텐츠에 사용자 입력이 필요한 경우, 레이블 또는 지침이 제공되어야함.

  ##### 3.3.3 오류 제안 (AA)
  - 입력 오류가 자동으로 감지되고 수정에 대한 제안이 알려진 경우, 콘텐츠의 보안이나 목적을 저해하지 않는 선에서 사용자에게 제안사항이 제공되어야 함. **ex)특수문자를 포함시켜주세요**

  ##### 3.3.4 오류 예방: 법률,재무,자료 (AA)
  - 사용자에 대한 법적 약속 또는 금융 거래가 발생하거나, 데이터 스토리지 시스템에서 사용자 등록 가능 데이터를 수정 또는 삭제하거나, 사용자 테스트 응답을 제출하는 웹 페이지의 경우, 다음 중 하나 이상을 지원해야함
    - **되돌림** : 제출된 것을 되돌릴 수 있어야 함.
    - **체크** : 사용자는 입력된 데이터를 입력 오류 체크 후, 수정할 기회를 제공 받아야 함.
    - **확인** : 제출을 마무리하기 전에 정보를 검증, 확인, 수정 할 수 있는 기능을 제공해야 함.

  ##### 3.3.5 도움말 (AAA)
  - 상황에 맞는 도움말을 제공.

  ##### 3.3.6 오류 예방: 공통 (AAA)
  - 4번과 동일.

---
### 4. 견고 (Robust)
- 사용자가 이용하는 모든 기기 및 브라우저에서 접근, 사용 가능해야 합니다.

#### 4.1 호환성
- 보조 기술을 포함하여 현재, 미래의 도구와 호환성을 높여야 함.

    ##### 4.1.1 해석 (A)
    - **문법오류 없게 마크업 제대로 하기!**

    ##### 4.1.2 이름, 역할, 값 (A)

    ##### 4.1.3 상태 메시지 (AA)
    -  **aria-live 사용**
    - ex) 회원가입 시 아이디 중복, 비밀번호 틀림 등의 상태 메세지
    - 오류 메시지 및 경고는 상태 메시지가 될 수 있지만 초점을 오류로 설정하여 컨텍스트를 변경해서는 안됨.

</div>
</details>