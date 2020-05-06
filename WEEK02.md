# TIL
오늘 내가 배운 것들(Today I Learned)   

---------------------------------------

#### 2주차 질문
- Q. 가상요소 사용 `::before`, `::after`를 사용하여 **텍스트** 를 삽입 할 경우, CSS를 제거한 환경에서는 해당 내용이 나타나지 않을 텐데요.. 웹접근성엔 맞지 않는 건가요?
```
  A.일반적으로 CSS를 제거한 환경을 사용자가 사용하는 경우가 희소하므로 특수한 상황일 듯 생각되고,
  그러한 경우까지 고려해서 개발하려면 개발자들의 스트레스 가중치가 높아 생명이 단축될 듯 합니다
  그리고 웹 접근성은 특정 환경, 특정 기술 사용에 국한되어 사용에 제약이 있을 경우 문제를 삼을 텐데...
  기본적으로 HTML, CSS를 따로 때어놓고 생각하는 상황이 없을 듯 합니다.

  'Windows, Mac, Linux , Web Browsers'와 같은 운영체제 또는 웹 브라우저 환경에서 접근 가능해야 하고,
  'Adobe Flash / Microsoft Silver Light / Microsoft ActiveX' 와 같이 특정 플러그인 기술에 종속되서는
  안되는 것이 접근성에 가깝지 않나 생각됩니다.

  웹브라우저들이 웹표준을 준수하지 않았던 시대에 웹표준 준수를 독려하며 벌였던 캠페인으로 CSS Naked Day가 있었습니다.
  해당 캠페인은 매년 4월 둘째주 특정 요일에 CSS를 배제하고 HTML만 제공하는 것이었죠.
  이 캠페인에 동참한 사이트들은 CSS Naked Day에 CSS를 배제한 채 날것의 HTML로 구성된 콘텐츠만 제공했었답니다.^^

  그런 관점에서 본다면 CSS를 이용하여 ::before와 ::after등의 가상 요소를 이용하여 정보를 제공하기 보다는
  HTML에 직접 정보를 제공하는 것이 웹접근성 측면에서는 더 나은 선택일 수 있다고 생각합니다.
```

---------------------------------------

## 표현 디자인(CSS)
<details open>
<summary>6일차 학습</summary>
<div markdown="6">

#### [CSS란?]
 - Cascading Style Sheets
 - HTML 문서를 스타일링 하는 언어
 - https://www.w3.org/Style/CSS/current-work
 - https://developer.mozilla.org/ko/docs/web/css
 - https://caniuse.com/

#### [기본 문법 & 스타일 방법]
```CSS
  선택자 {
    속성1: 값;
    속성2: 값2;
  }
```
- 인라인 스타일 (inline style) : 요소 내부 포함
  ```html
    <section style="color:#903000">
      ...
    </section>
  ```
- 인터널 스타일 (internal style) : `<head>`에 포함
  ```html
  <head>
    <style>
      section{color:#903000;}
    </style>
  </head>
  ```
- 익스터널 스타일 (external style) : CSS 파일을 HTML 문서에 연결
  ```html
    <link rel="stylesheet" href="css/style.css">
  ```

#### [심플 선택자]
- 요소(타입,태그) 선택자(Element Type Selector) `h1{ ... }`
- 그룹핑(Grouping) `a, abbr{ ... }`
- 유니버설(전체) 선택자(Universal Selector)  `*{ margin:0; padding:0; }`
- 자손 선택자(Descendent Selector) `h1 abbr { ... }` `.class1 .class2 { ... }`
- 클래스 선택자(Class Selector) `.class { ... }`
- 멀티클래스 선택자(Multi Class Selector) `.class1.class2 { ... }`
- 아이디 선택자(ID Selector) ` #id { ... }`


#### [속성 선택자]
- 자식 선택자 : 자손 선택자와 다름, **직계자손** 만!!  `p > img { ... }`
- 속성 선택자
  ```CSS
    div [id="about-css"]{ ... }
     div#about-css { ... }
    p [class="note"] { ... } /*특정단어를 정확히 일치하는 경우*/
     p.note { ... }    
    area[shape][title]{ ... }
  ```
- 고급 선택자
  ```CSS
    abbr [title~="mobile"] { ... } /*특정단어를 포함하는 경우*/
    img [alt|="love"] { ... } /*대시(-)로 구분되는 경우*/
    a [href^="http://"] { ... } /*특정단어로 시작하는 경우*/
    a [src$=".svg"] { ... } /*특정단어로 끝나는 경우*/
    abbr [src*="phone"] { ... } /*특정단어를 포함하는 모든 경우*/
  ```
- **대소문자 구분!**

#### [가상 클래스(Pseudo Class) 선택자]
- 콜론 하나 사용 `:`   

  ```CSS
    :link         { ... } /*기본 상태*/
    :visited      { ... } /*방문한 상태*/

    :hover        { ... } /*마우스를 올라간 상태, 마우스에 의존*/
    :active       { ... } /*클릭한 순간의 상태, 마우스에 의존*/

    :focus        { outline-offset:3px; outline:3px solid #333; }/*포커스된 상태, 키보드에 의존*/
    :focus:hover  { ... }
    :focus:active { ... }

    :first-child  { ... } /*첫번째 자식*/
    :last-child   { ... } /*마지막 자식*/
    :nth-child(n) { ... } /*홀수(odd), 짝수(even), 포뮬러 공식사용 가능 ex)3n*/

    :lang(ko-KR){ font-family: "Spoqa Han Sans"; }
    :lang(en){ font-family: "Times New Roman"; }
  ```
#### [가상 요소(Pseudo Element) 선택자]
- 콜론 2개 사용 `::`   

  ```CSS
    ::first-letter { ... } /*첫번째 글자*/
    ::first-line   { ... } /*첫줄 문자 - 동적으로 찾아줌*/
    ::before       { ... }
    ::after        { ... }
  ```

</div>
</details>

---------------------------------------
<details open>
<summary>7일차 학습</summary>
<div markdown="7">

#### [상속]  
- 상속되는 속성 (글자색, 글자 디자인에 관련된 것)
  - `color` / `font-size` / `font-family` / `letter-spacing`
- 상속되지 않는 속성 (공간에 관련된 것)
  - `outline` / `margin` / `border` / `padding`

#### [우선 적용 규칙]
- 캐스케이드(Cascade) 규칙 : 여러 개의 CSS 파일을 결합할 때, 충돌을 해결하는 프로세스.
> #### Cascade???
>> Cascade는 '종속'이라는 의미로 일단 개시되면 각 단계가 전 단계로 인하여 발동되고 그 결과 종국까지 연속되는 단계의 계열을 말합니다. 원래 의미는 기근으로 분리되어 떨어지는 폭포를 뜻합니다.

##### 1. 중요성 (Importance)
  -  `!important` 선언은 다른 모든 선언보다 우선권을 가진다.
  - [NOTE] !important가 적용된 속성을 덮어 쓰려면, 다시 !important를 사용해야 하기에 **최대한(절대!!) 사용하지 않도록 노력** 해야 한다.

##### 2. 특성 (Specificity)
  - 선택자의 우선권에 대한 척도.
  - 각 척도를 1, 10, 100, 1000 단위로 생각하면 이해하기 좋다.
    ```
      요소 선택자 < 클래스 선택자 < ID 선택자 < 인라인 스타일
        0,0,0,1      0,0,1,0      0,1,0,0      1,0,0,0
    ```
  - [NOTE] `*`, `>`, `+`, `~` 등 콤비네이터(Combinators),`:not()` 가상 클래스는 특성에 영향을 주지 않는다.   

    ```
     [예시]
       *                         -- 0000
       a                         -- 0001
       .link                     -- 0010
       a[href]                   -- 0011
       li:nth-child(2) a:hover   -- 0022
       .nav:nth-child(2) a:hover -- 0031
       #outer a                  -- 0101
       #outer #inner a           -- 0201
       style="color: tan"        -- 1000
                                 -- !important
    ```
##### 3. 소스 순서
  - 중요성, 특성이 설정되지 않았거나 동일한 경우 **나중에 나온 소스** 의 스타일이 우선권을 가진다.
    ```css
       p { color: #930212; }
       p { color: #d5727e; } /*우선권을 가진다.*/
    ```

#### [타이포 그래피]
##### 1. 폰트(Fonts) 스타일 속성
  - 폰트에 영향을 주는 속성으로 적용되는 `font-family` 모양 / `font-size` 크기 / `font-weight` 굵기 /`font-style` 기울임(이탤릭) 등 / `font-variant`  등.
  - ※ 글자 색상은 `color` 속성으로 설정.   

    ```
      1. color keywords
        - red, gree, blue, pink, black
      2. hex color code
       - #RRGGBB / 0 ~ 9, a ~ f 예)#1868a7
      3. rgb, rgba
       - RED, GREEN, BLUE, ALPHA 예)rgba(127,255,0,0.3)
      4. hsl, hsla
       - HUE, SATURATION, LIGHTNESS, ALPHA 예)hsla(360,60%,70%,1)
    ```
  - ※ 웹브라우저는 운영체제가 지원하는 기본 폰트(웹 안전 폰트)만 화면에 렌더링 한다. (참고: https://cssfontstack.com) 즉, 사용된 폰트가 사용자 컴퓨터에 없으면 렌더링 X.
    ```
      [웹 안전 폰트]
      Arial            [sans-serif]  고딕체
      Verdana          [sans-serif]  고딕체
      Courier New      [monospace]   코드체(공간이 동일)
      Georgia          [serif]       명조체
      Times New Roman  [serif]       명조체
      Trebuchet MS     [serif]       명조체
    ```
  - ※ 비주얼 디자인 과정에서 적용 가능한 웹폰트를 사용해야 한다. 폰트 저작권에 주의!
  - ※ 저작권 걱정 없는 폰트
    - https://fonts.google.com
    - https://google.co.kr/search?q=무료+웹폰트

##### 2. 텍스트(Text) 레이아웃 속성
  - 텍스트 간격 및 레이아웃 기능에 영향을 주는 속성으로 행간, 자간, 어간, 정렬, 변형, 꾸밈, 그림자
    - `line-height` 행간 - 최소 1.5이상이 글읽기에 용이
    - `letter-spacing` 자간 - em단위로 설정하는것이 좋음.   

      ```
        디자이너가 '-20'으로 설정
        letter-spacing: -0.02em; (-20/1000em)
      ```
    - `word-spacing` 어간 (단어사이의 간격)   

    ```
      ※행간 > 어간 > 자간 - 가독하기가 쉬워짐.
    ```
    - `text-align` 정렬 - left(기본값) / center / right
    - `text-indent` 들여쓰기
    - `text-transform` 변형 - uppercase(모두 대문자) / lowercase(모두 소문자)
    - `font-variant` 변형 - small-caps(대문자만 크게, 소문자는 작은대문자) / all-small-caps(모두 작은 대문자)
    - `text-decoration` 꾸밈 - underline(밑줄) / overline(윗줄)/ line-through(중간줄)
      - 글자를 판독하기 어렵기때문에 권장하지 않음

    - `white-space` 공백처리
      - `normal` 기본값 - 공백을 여러개 넣어도 1개만 표시 / 자동줄바꿈
      - `pre` - 공백을 있는 그대로 표시 / 줄바꿈X
      - `pre-line` - 공백을 있는 그대로 표시 / 들여쓰기 제거 / 자동줄바꿈
      - `nowrap` - 공백 1개만 표시 / 줄바꿈
    - `word-break` - 단어의 분리를 어떻게 할 것인지 결정
      - `break-all`   

        ```
          (공백/띄어쓰기) 수고했어.오늘도
          (음절)         수.고.했.어.오.늘.도
        ```
    - `word-wrap` - 박스의 가로 영역을 넘친 단어 내에서 임의의 분리 여부를 결정하여 줄바꿈에 관여
      - `break-word`
    - `text-shadow` 그림자
      ```css
        /*text-shadow : x y blur sprea color;*/
        h1 { text-shadow : 4px 4px 0px #9bdbde, 0px 3px 10px #943978;}   
      ```

- (참고)기타 단위 `px` 고정값 / `em` 상대값

</div>
</details>

---------------------------------------
<details open>
<summary>8일차 학습</summary>
<div markdown="8">

#### [박스 모델]
-  CSS를 사용해 HTML 요소를 레이아웃(배치) 하려면 박스 모델에 대해 먼저 이해해야 한다.   


##### 1. `block` vs `inline` vs `inline-block` 요소간 특성에 대한 이해
- `block` 요소 (HTML5 : Flow Contents)
  - 블록박스는 다른 블록 박스에 포함되거나, 포함할 수 있음.
  - 너비(width) / 높이(height) 설정이 가능.
  - 내부에 콘텐츠를 포함하지 않을 경우 높이는 `0`   

    <details open>
    <summary>block 요소들</summary>
      <div markdown="8_1">

      - address
      - article
      - aside
      - audio
      - blockquote
      - canvas
      - dd
      - div
      - dl
      - fieldset
      - figcaption
      - figure
      - footer
      - form
      - h1~6
      - header
      - hr
      - noscript
      - ol
      - output
      - p
      - pre
      - section
      - table
      - tfoot
      - ul
      - video

      </div>
    </details>

- `inline` 요소 (HTML5 : Phrasing Contents)
  - 인라인 박스는 다른 인라인 박스에 포함되거나, 포함할 수 있지만, **블록요소** 는 포함할 수 없음.
  - 너비(width) / 높이(height) 설정이 불가.
  - 내부에 포함한 콘텐츠만큼 높이와 너비를 가지게 됨.   
  - **좌/우** 방향으로 `margin`, `padding` 공간을 설정할 수 있으나, **상/하** 방향으로는 공간이 설정되지 않음.

- `inline-block`
  - 인라인 블록 박스는 기본적으로는 인라인처럼 화면에 렌더링됨.
  - 블록박스처럼 **너비(width) / 높이(height) 설정이 가능** (`<img>`, `<input>`, `<button>` 등)

##### 2. `margin` vs `border` vs `padding` vs `content` 박스 간 특성에 대한 이해
- `margin-box` - 외부 공간 박스 / 박스와 박스 사이의 간격 (배경색 X, 투명공간) / 음수값 사용 가능

  ```
    * margin-top / margin-right / margin-bottom / margin-left
    * margin: t r b l
    * margin: t r b (l=r)
    * margin: t r (b=t) (l=r)
    * margin: t (r=t) (b=t) (l=r)
  ```   

- `border-box` - 테두리 공간 박스 / 배경색O / 음수값 사용X

  ```
    * border-(top|right|bottom|left)-width
    * border-(top|right|bottom|left)-style
    * border-(top|right|bottom|left)-color
    * border: width style color
    * border-top: width style color
    * border-right: width style color
    * border-bottom: width style color
    * border-left: width style color
  ```   

- `padding-box` - 내부 공간 박스  / 배경색O / 음수값 사용X

  ```
    * padding-top / padding-right / padding-bottom / padding-left
    * padding: t r b l
    * padding: t r b (l=r)
    * padding: t r (b=t) (l=r)
    * padding: t (r=t) (b=t) (l=r)
  ```   

- `content-box` - 콘텐츠 공간 박스

##### 3. `dimension` & `box-sizing` & `overflow` 속성 사용에 대한 이해
- DIMENSION
  - `width`       --  박스 너비
  - `height`      --  박스 높이
  - `min-width`   --  박스 최소 너비
  - `min-height`  --  박스 최소 높이
  - `max-width`   --  박스 최대 너비
  - `max-height`  --  박스 최대 높이    

- BOX SIZING
  - `content-box`(default) : `padding`과 `border`를 포함X
    - width = content-box
    - height = content-box
  - `border-box` : `padding`과 `border`를 포함
    - width = content-box + padding-box + border-box
    - height = content-box + padding-box + border-box

- FLOW
  - `overflow` : 박스를 넘쳐난 상태(흐름) 조정
    - `auto` 넘치면 자동 스크롤  / `visible` 다 보여줌 / `hidden` 숨기기 / `scroll` 기본적으로 스크롤을 보여줌
  - `overflow-x` , `overflow-y`

#### [리스트 스타일링]
- `ul` 비 순차 목록: Unordered List
  - `list-style-type`
    - disc / circle / square / upper-alpha (A,B,C...) / lower-alpha (a,b,c...) / decimal (1,2,3...) / decimal-leading-zero (01,02,03...)/ hangul
  - `list-style-position` : outside / inside
  - `list-style-img` : url("star.svg")
  - `list-style` : square url("star.svg") inside  - 속기 유형 작성법   

    ```css
      ul{ list-style: none inside url("../images/stat.svg") }
    ```   

  - 가상요소를 사용하여 스타일링
    ```css
      ul{ list-style: none; }
      li::before{ content: '-⁜-'; color: #474cc5; margin-left:1em; }
    ```

- `ol` 순차 목록: Ordered List   
  - `start` 시작번호 입력 or `li` 요소에 value값 지정
  - `reversed` 역순서   

    ```html
      <ol start="10" reversed>
        <li>...</li>
        <li value="10">...</li>
        <li>...</li>
      </ol>

    ```   

- `dl` 설명 목록: Definition List - `<dt>`, `<dd>`

```
  [참고]
  - rem 단위 : root em - html font-size에 대한 상대값
```   

#### [배경 스타일링]
- `background-color` 배경 색  : transparent(기본값 : 투명)
- `background-image` 배경 이미지
- `background-repeat` 배경 반복 : repeat(기본값) / no-repeat /  repeat-x /  repeat-y
- `background-position` 배경 위치 : 키워드(left/center/right/top/bottom), px, %
- `background-attachment` 배경 고정 : fixed(스크롤 움직임에 따라 배경 고정.)
- `background-size` 배경 크기
  - contain : 배경을 사용하는 **요소를 벗어나지 않는 최대 크기** 로 이미지를 확대 또는 축소. 비율을 유지.
  - cover : 배경을 사용하는 **요소를 다 채울 수 있게** 이미지를 확대 또는 축소. 비율을 유지.

  ```css
    .bg-image {
      background-color: #000999;
      background-image: url("../images/filename.jpg");
      background-repeat: no-repeat;
      background-position: 10px 40px;
      background-attachment: fixed;
      background-size: 100px;
    }
    .bg-image {
      background: #000999 url("../images/filename.jpg") no-repeat 10px 40px fixed;
      background-size: 100px;
    }
  ```  
- `background-origin` 배경 기준 : padding-box(기본값) / border-box / content-box
- `background-clip` 배경 클리핑 : initial(기본값) / padding-box  / border-box / content-box   

  ```css
    .background-clip {
      box-sizing: border-box;
      border-radius: 20px solid rgba(0,0,0,0.2);
      padding:20px;
      background: url(../images/model.jpg) center;
      background-size: contain;      
      background-origin : content-box;
      background-clip: padding-box; /*다른 속성들보다 아래있어야 적용됨*/
    }
  ```

</div>
</details>

---------------------------------------
<details open>
<summary>9일차 학습</summary>
<div markdown="9">

#### [플로팅 레이아웃]
- 일반적인 레이아웃 흐름(Normal Layout Flow)
  - HTML이 기본적으로 화면에 렌더링하는 것을 말함. **마크업 순서대로 위에서 부터 아래 방향으로 나열**(CSS 미반영)      

- 플로팅 레이아웃(Floating)
  - float 속성을 사용해 박스를 왼쪽 또는 오른쪽으로 `부유`시키는 레이아웃 기법.
  - `none`(기본값) / `left` / `right`   
  - 플로팅 레이아웃을 사용하면 컬럼 레이아웃 디자인을 손쉽게 구현할 수 있음.

##### **레이아웃 틀어짐  해결 방법**
1. `clear:both;` - 자식들의 높이를 부모가 인식할수 있도록 해줌.   

    ```html
      <div class="box-group">
        <div class="box is-blue"></div>
        <div class="box is-yellow"></div>
        <div class="box is-green"></div>
        <div class="clear"></div>
      </div>

      <style>
        .clear{clear:both;}
      </style>
    ```   

2. `overflow`
    - 부모요소에 css:`overflow` 속성 추가 - 권장하지는 않음.
3. `::after`
    - 부모요소에 가상요소 선택자 `::after`사용. - 권장   

     ```css
      .clearfix::after{ content: ''; display: block; clear:both;}
      .is-blue{ float: left; }
      .is-yellow { float: left; }
      .is-green  { float: left; }
     ```

#### [포지셔닝 레이아웃]
- 포지셔닝은 웹브라우저가 렌더링하는 기본 레이아웃 흐름을 **재정의** 하여 흥미로운 효과를 만들어 낼때 사용.
- 예를 들어 기본 레이아웃 흐름에서 레이아웃 내부 일부 요소의 위치를 조정하려면 포지셔닝을 사용하여 조정할 수 있음.
- 페이지의 다른 부분 위에 떠있는 UI 요소를 만들고 싶거나, 페이지의 스크롤과 상관없이 항상 브라우저 창의 동일한 위치에 자리한 UI요소를 만들고자 한다면 포지셔닝을 사용

##### 포지셔닝 레이아웃 유형
- 정적(static)위치 - 기본값   

- 상대(relative) 위치 - 원래 위치 기준. 자신이 가지고 있는 박스 크기 기준.
  ```css
    .is-blue{ position:relative; top:30px; right:-100px;  z-index: 1}
  ```
- 절대(absolute) 위치
  - 가장 가까운 부모요소 중 포지션값이 설정된 것 기준.(static이 아닌 것)
  - 설정된 부모가 없을 경우 - 뷰포트 기준
  - 부모요소 설정 필요
    ```css
      .box-group{ position:relative;} /*부모요소 설정*/
      .is-yellow { position:absolute; top:0; left:10px; }
    ```   

- 고정(fixed)  - 사용자가 보는 뷰포트 기준
  ```css
    .box-group{ position:relative;}
    .is-yellow { position:fixed; top:0; left:10px; }
  ```   

- 달라붙는(sticky) 위치
  - 평소에는 상대(relative) 위치로 처리하지만, 부모요소 기준으로 지정한 임계값을 넘으면 마치 fixed처럼 화면에 고정. 고정 상태는 부모요소의 반대편 모서리를 만나면 해제.
  - IE 브라우저 미지원 / Javascript 사용시 9이상에서 가능.
  ```css
    .box-group .box { position: sticky; top:0; }
  ```   

- `z-index`
  - 숫자값이 높을수록 앞에 배치됨.
  - 값이 동일할 경우 마지막으로 마크업된 요소가 앞에 배치.
  - 10,100 단위로 관리 - 중간 수정 시 용이.

- `transform : translateX(-50%)`
  - 자신의 크기의 절반만큼을 왼쪽으로 이동. **가운데 배치에 유용** / IE9이상 사용가능.
    ```css
      #schema .lix-pen{
        position: absolute;
        top:30px;
        left:50%;
        transform: translateX(-50%);
      }
    ```

</div>
</details>

---------------------------------------
<details open>
<summary>10일차 학습</summary>
<div markdown="10">

#### [테이블 스타일링]
- 복잡한 정보를 효과적으로 사용자에게 보여주고자 할 때 사용하는 테이블 스타일링.
- 테이블은 복잡한 정보를 제공하기에 특히 **접근성을 고려** 해서 디자인/스타일링 해야함.
- 접근성을 고려하여 테이블 **제목(Caption)** 또는 **테이블 요약(Summary)** 내용을 구조화 할것.
- 디자인의 본질은 사람이고, 사람을 위한 디자인이 우리의 목표

##### 구조화는 되었으나, 화면에서 감춰야 할때
```CSS
  /* 접근성(accessibility, a11y)을 고려한 화면 감춤 */
  .a11y-hidden {
    overflow: hidden;
    position: absolute;
    clip:     rect(0,0,0,0);
    width:    1px;
    height:   1px;
    margin:   -1px;
    border:   0;
    padding:  0;
  }

  /* 화면에 표시되는 caption 요소의 공간 제거를 위한 설정 */
  caption.a11y-hidden {
    position: static;
  }
```

1. 테이블, 셀(제목/내용)의 테두리(border)를 디자인 할 수 있음
2. 테이블 셀 사이 간격을 접거나(collapse), 나눌(separate) 수 있음.
3. 테이블 테두리 사이 간격을 설정할 수 있음.(`border-collapse:separate;` 설정 필요)
    - 일반적인 테이블 디자인 시 잘 사용하지 않음.
    ```css
      table{ border-collapse: separate; border-spacing: 10px;}
    ```
4. 테이블 캡션 위치(top, bottom)를 설정 할 수 있음.
5. 테이블 레이아웃(auto, fixed) 설정을 통해 콘텐츠의 양에 따라 셀의 크기를 변경하거나, 고정 할 수 있음
    - auto : 테이블 셀 내용이 많아지면 자동으로 늘어남.
    - fixed : 테이블 셀 내용이 많아져도 자동으로 늘어나지 않음. **width 설정 필요.**

6. `<th>`, `<td>`은 마진(margin)이 설정 X.
7. `<th>`, `<td>`은 패딩(padding)은 설정 O.
8. 빈 셀(empty cell)의 표시(show/hide) 설정이 가능.
    - hide 설정 시 빈 셀은 화면에 그려지지 않음.

  ```css
    table, th, td{ border:1px solid #333;} /* 1. border */
    table{
      border-collapse: collapse; /* 2. collapse / separate(기본값) */
      caption-side : bottom; /* 4. 캡션 위치 설정 - bottom / top(기본값) */
      table-layout: fixed; width:600px; /*5. fixed / auto(기본값)*/
      empty-cells: hide; /* 8.셀 숨김 처리*/
    }
    th, td{ padding:4px 10px;} /* 7. padding설정 */

  ```

#### [폼 스타일링]
- 사용자가 입력된 내용의 상태를 이해하고 대처할 수 있도록 고려하여 설계.

###### `The Good` CSS를 사용해 완벽하게 스타일링 할 수 있는 요소들
- `<form>`
- `<fieldset>`
- `<label>`
- `<output>`

##### `The Bad` CSS를 사용해 완벽하게 스타일링 할 수 없는 요소들
- `<legend>`
- `placeholder` 속성

##### `The Ugly` CSS를 스타일링이 전혀 적용되지 않는 요소들
- `<select>`
- `<optoion>`
- `<optgroup>`
- `<datalist>`
- `<progress>`
- `<meter>`

##### 폼 컨트롤 가상 클래스(Pseudo Classes)
1. IE9+
  - `:checked` 컨트롤 체크 상태 표시   
    - `<input type="radio">` / `<input type="checkbox">` / `<option>`
  - `:enabled`/`:disabled` -  활성화/비활성화된 컨트롤 상태 표시
  - `:indeterminate` 불확실한 상태의 컨트롤 표시

2. IE10+
  - `:required` 필수 컨트롤의 상태 표시
    - `<input>` / `<textarea>` / `<select>`
  - `:optional` 선택 컨트롤의 상태 표시
    - `<input>` / `<textarea>` / `<select>`
  - `:valid` / `invalid` - 유효한/유효하지 않은 컨트롤의 상태 표시
    - `<input>` / `<form>`
    - ex) mail 형식

3. IE x
  - `:default` 컨트롤 기본 상태 표시
    - `<button>` / `<input type="checkbox">` / `<input type="radio">` / `<option>`
  - `:in-range`/`:out-of-range` min,max값을 가지는 input 컨트롤의 허용/비허용범위 상태 표시
  - `:read-only` / `:read-write` 읽기만 가능 / 읽기-쓰기 가능
    - `<input>` / `<textarea>`

##### 실습 참고사항
```CSS
  .modal-form label {
    user-select: none; /* 텍스트 선택 불가 (더블클릭으로 인한 드래그) */
  }
```
- [폼스타일링] https://developer.mozilla.org/en-US/docs/Learn/Forms/Styling_web_forms
- [폼스타일링 고급] https://developer.mozilla.org/en-US/docs/Learn/Forms/Advanced_form_styling
- [커스텀 폼 컨트롤 만들기] https://developer.mozilla.org/en-US/docs/Learn/Forms/How_to_build_custom_form_controls


</div>
</details>
