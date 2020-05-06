# TIL
오늘 내가 배운 것들(Today I Learned)   


---------------------------------------
#### 1주차 질문
- ~~Q.혹시 GitKraken을 사용하는 이유가 있나요? 현재 Atom에디터를 사용중인데 Atom에 GitHub연동하여 사용해도 되나요?~~
- Q. strong,em,b,i 시각장애 음성지원 사용시 4개가 다 다르게 읽히나요?
  ```
    A."아니오" 입니다.
    strong나 em 요소는 의미론적으로 강조의 뜻을 가지고 있으며
    스크린리더가 해당 요소를 음성의 변화나 다른 방법으로
    사용자에게 전달할 수 있는 옵션을 제공한다는 의미로 생각하시면 됩니다.
  ```
- Q. SVG는 확대해도 깨지지 않는데, 그럼 canvas보다 svg 방식을 사용하는게 좋은건가요?
  ```
    A. SVG는 벡터 이고 <canvas>는 비트맵 입니다.
    SVG를 사용할 수 있는 환경이라면 당연히 비트맵 형식보다
    많은 장점을 가지기 때문에 권장하고 싶습니다.
    그러나 <canvas>가 필요한 경우도 있으니 상황에 맞게 적절한 방식을 사용하시면 됩니다.
  ```
- Q. 웹접근성을 고려한다면 noscript는 필수적으로 넣어야하는 건가요?
  ```
    A. <noscript> 요소가 필수라고 볼 수는 없습니다.
    그러나 <script>를 지원하지 않는 환경을 위한 대안으로 제공할 경우라면
    <noscript> 가 웹접근성 측면에서 필요할 수 있습니다.
  ```
- Q. accesskey가 브라우저와 운영체제 플랫폼에 의존한다하셨는데, 웹접근성을 고려하여 동일한 단축키를 제공하려면 Javascript를 사용해야하나요?
  ```
    A. 말씀하신 것처럼 동일한 단축키를 제공하고자 한다면 Javascript를 사용하여야 합니다.
    이런 측면에서 본다면 사실 HTML의 accesskey 속성이 의미가 없게 느끼실 수도 있을 것 같습니다.
  ```

## 구조 디자인(HTML)
<details open>
<summary>1일차 학습</summary>
<div markdown="1">

#### [HTML 이란?]
- HTML (HyperText Markup Language)
- 확장자 `.html`
- 웹사이트 콘텐츠를 설명하는데 사용되는 마크업 언어
- HTML은 콘텐츠의 의미를 설명하는데 유일한 목적을 가집니다. 비주얼 디자인(모양, 색, 크기 등)이 목표가 아니라, **구조 설계(Structure Design)** 를 목표로 합니다.

시멘틱 마크업]
- Semantic Markup :  종종 POSH(Plain Old Semantic HTML)라고도 불리우는데 말 그대로 **평범하고 오래된 의미론적인 HTML** 이라는 뜻.
  ```html
    <h1></h1> <!--제목 heading-->
    <p></p> <!--단락 paragraph-->
  ```

#### [기본 문법]
- HTML 웹 페이지는 헤드(head) 영역과 바디(body) 영역으로 구성
  - 타이틀(title)은 웹 페이지의 제목으로 브라우저 탭에 표시
- element : tag name / attribute name, value
- `<태그이름 속성="값">컨텐츠</태그이름>`
```html
  <html>
    <head>
    <meta characterSet="UTF-8">
      <title>HTML 문서 작성을 위한 기본 문법</title>
    </head>
    <body>
      <p title="Development Tools">개발도구(DevTools)</p> <!--title속성 : 툴팁제공-->
    </body>
  </html>
```
- (참고) console창 > document.characterSet 입력 >  문자 인코딩 반환 (UTF-8).


#### [텅 빈 요소]
- meta : 내용컨텐츠를 감싸지 않아 닫는 태그가 필요 없음. (empty element)


#### [표준 호환모드]
- html(root) : html 요소는 오직 1개의 head와 뒤 따르는 1개의 body 요소만 자식으로 포함
- DTD : 문서 유형 정의(Document Type Definition)
- 브라우저의 렌더링 모드를 표준으로 작동하게 만들어 줌. DTD는 HTML 문서의 반드시 최상 위에 위치해야 함.
  ```html
    <!DOCTYPE html> <!--웹표준문서-->
  ```

#### [주 언어 설정]
- **KR** : Republic of Korea 지역(locale) 정보. ko 만 사용하면 한국어를 통칭
- (참고) en-GB ⇒ 영국 영어 / en-US ⇒ 미국 영어 / en-CA ⇒ 캐나다 영어
  ```html
    <html lang="ko-KR"> <!--ko/en/es/ja 등..-->
  ```

#### [제목과 단락]
- `<h1>` 제목(Headings) - 제목 레벨(Level) : 1~6단계
  - 1단계는 문서에서 1번만 사용 / HTML5부터는 섹션 콘텐츠마다 사용 가능.
  - 2단계부터는 여러개의 제목을 사용할 수 있다.
- 주석 : 브라우저에서 해석되지 않음.
- `<p>` 단락 : Paragraph   

```html
  <h1></h1>
  <h2></h2>
  <h3></h3>
  <h4></h4>
  <h5></h5>
  <h6></h6>
  <!--주석-->
  <p>단락</p>
```

#### [이미지와 피규어]
- `<img>` : image 태그
- `<figure>` : 이미지, 차트, 도표 등을 감싸는 태그
- `alt` alternative : 대체텍스트, **이미지를 분석하여 묘사할것.**
  - 속성을 잘 설정해두면, 시각 장애인이 아니더라도 도움을 받을 수 있음.
  - 이미지 링크가 깨질 경우, 화면에 alt 속성 값이 출력 되어 어떤 이미지 였는지 정보를 제공할 수 있음.   

```html
<figure>
  <img src="" alt="대체 텍스트">
  <figcaption>이미지 출처 등 캡션</figcaption>
</figure>
```

#### [문법 검사]
- [validator.w3.org](https://validator.w3.org) : 문법 유효성 검사
- [entitycode.com](https://entitycode.com) : entitycode
  ```html
    &lt; &gt; &copy; &midot; &nbsp; &amp;
  ```


#### [순차/비순차 목록]
- `<ul>` unordered lists 비순차 목록
- `<ol>` ordered lists 순차 목록
- `<li>` list Item

</div>
</details>

---------------------------------------
<details open>
<summary>2일차 학습</summary>
<div markdown="2">

#### [앵커와 하이퍼링크]
- `<a>` anchor : 현재 페이지에서 위치 이동
- `href` hyperlink : 다른 창으로 이동. a 요소에 href 속성을 사용하여 링크 주소를 설정
  - `target="＿blank"` 새창(새탭)열림
  - `href="mailto:"` 이메일 링크   

```html
  <!--anchor-->
  <a href="#intro">소개</a>
  <h3 id="intro">소개</h3>

  <!--hyperlink-->
  <a href="http://naver.com" target="_blank">
    <img src="img경로" alt="NAVER logo" />네이버
  </a>
```
- 절대 / 상대 / 루트 경로
  - URL(Uniform Resource Locators)
  - `http://` <sub>Scheme</sub> `developer.mozilla.org` <sub>Domain</sub> `/en-us/docs/web/html` <sub>Path</sub>
  - **절대경로** (absolute path)
    - HTML 문서와 상관없이 URL 주소를 사용해 리소스를 찾는 것
    ```
      "http://domain.com/resource.html"
    ```
  - **상대경로** (relative path)
    - 현재 HTML 문서에서 상대적인 위치를 설정하는 것
    ```
      "../misc/extras.html"
    ```
  - **루트 상대경로** (root-relative path)
    - 현재 HTML 문서가 존재하는 영역의 최상위 루트 경로에서 대상을 찾는 것
    ```
      "/images.html"
    ```

#### [설명 목록]
- `<dl>` 설명목록(Description lists)
- `<dt>` 용어(Definition Term)
- `<dd>` 설명(Definition Description)
```html
  <dl>
    <!--1-->
    <dt>용어</dt>
    <dd>설명</dd>
    <!--2-->
    <dt>용어</dt>
    <dt>용어</dt>
    <dt>용어</dt>
    <dd>설명</dd>
    <!--3-->
    <dt>용어</dt>
    <dd>설명</dd>
    <dd>설명</dd>
    <dd>설명</dd>
  </dl>
```

#### [인용과 줄 바꿈]
- `<q>` quote
  - 짧은 인라인 인용문. ("") 사용가능 / 강조용으로 쓰인 경우 &lt;q&gt; 사용 불가. / 중첩가능
- `<blockquote>` : 긴 인용문
- `<cite>` citation : 출처 정보
```html
  <p>
    <q cite="출처정보">컨텐츠 인용시 사용 <q>중첩가능</q></q>
    <cite>출처정보</cite>
  </P>
```
- `<br>` : 줄바꿈. **1번만** 사용

#### [어휘 요소들]
- 어휘 요소 활용 : strong, em, b, i
##### ▷ 강조 - 의미(Semantic Element)
- `<strong>`
  - 내용의 중요성(Importance), 심각성(Seriousness), 긴급성(Urgency)을 강조할 경우 / 중첩가능
  ```
    - [중요성] 제목/캡션의 글자 중 일부를 더욱 강조하는데 사용
    - [심각성] 경고 또는 주의를 주고자 할 때 사용
    - [긴급성] 문서의 다른 부분보다 빨리 보아야 하는 내용을 나타내는데 사용
  ```
- `<em>`
  - 특정 내용의 스트레스(Stress) 강조(Emphasis) - 문장 의미를 변경 / strong보다는 약한 강조   

##### ▷ 표현 - 의미가 없는 요소 (Non Semantic Element)
- `<b>`
  - 단순히 다른 글자와 구분된 용도로 사용.문서 요약의 주요 단어, 리뷰 제품 이름 등.
- `<i>`
  - 다른 글자와 구분된 용도로 사용. 기술적 용어, 다른 언어(목소리), 인물의 생각 등을 표현.

#### [섹션/메인 요소]
##### ▷ 루트섹션(Root Section) 요소
- `<body>` 문서에서 단 1번만 사용가능

##### ▷ 섹션(Sections) 요소들 : 컨테이너 요소 X(ex. div,span), 명시적으로 나열되는 경우에만 적합함. **제목(h1~h6)을 포함시켜 식별해야함.**
- `<article>` Article Section
  - 문서, 페이지, 애플리케이션, 사이트 등에 포함된 **독립적인** 섹션.
- `<section>` General Section
  - 문서, 애플리케이션의 **일반적인** 섹션. 주제별로 그룹화 된 콘텐츠
- `<nav>` Navigation Section
  - 다른 페이지로 이동하는 링크 또는 사이트 내 탐색 링크를 포함하는 섹션 요소. 비순차목록(ul) 사용
- `<aside>` Sidebar Section
  - 웹 사이트의 사이드바에 해당되는 부 콘텐츠(메인 콘텐츠와 불리된 섹션) - 광고 배너 등

##### ▷ 섹션 내부에 사용되는 요소들(섹션 내부에 넣어도 되고 넣지 않아도 됨.) / 섹션요소 X
- `<header>` Section Header
  - 제목, 로고, 검색, 내비게이션 등 포함
- `<footer>` Section Footer
  - 내비게이션, 저자, 사이트 정보, 저작권 등 포함

##### ▷ 메인(Main) 요소 / 섹션요소 X
- `<main>` 문서 또는 애플리케이션 body 요소의 메인 콘텐츠에 해당.
  - 보이는 요소가 2개 이상이면 안된다. 사용되지 않는 main요소는 화면에서 감춤(hidden) 처리 해야한다.
  - article, section, aside, nav 요소는 main 요소를 자식으로 포함할 수 없다. 반대로 main 요소는 섹션요소들을 포함할 수 있다.
    ```html
    <section><main></main></section> (X)
    <main><section></section></main> (O)
    ```
  - main 내부에는 header, footer 요소를 직접적으로 포함하지 않는다.
    ```html
    <main>
      <header></header> (X)
      <section><header></header></section> (O)
    </main>
    ```

</div>
</details>


---------------------------------------
<details open>
<summary>3일차 학습</summary>
<div markdown="3">

#### [컨테이너 요소]
- HTML 요소를 묶는 컨테이너 요소. 의미를 가지지 않음. 시각적 효과(CSS 적용 등)를 주기 위해 사용.
- `<div>` Division : block 컨테이너
- `<span>` 인라인(inline) 컨테이너. 인라인 요소를 감쌀 때 사용. 블록요소들을 감쌀수 없음.

#### [텍스트 레벨 요소]
- `<sub>` Subscript Text 아래첨자
  - 화학식, 수학식 ex)H<sub>2</sub>SO<sub>4</sub>
- `<sup>` Superscript Text 윗첨자
  - 각주 ex)각주<sup><a href="#footnote-1">[1]</a></sup>
- `<mark>`
  - 관련 참조 목적의 하이라이트된 글자 요소. 검색시 마킹효과
- `<abbr>` Abbreviation 축약
  - ex)맥날-맥도날드
- `<s>` Strikethrough 취소선
   - 더이상 관련이 없거나 더 이상 정확하지 않은 요소 ex)<s>11,900원</s> 5,900원
- `<time>`
  - 기계가 이해할 수 있는 형태로 날짜나 시간을 나타내는 요소   

```html
  <!-- sub -->
  <dfn id="sulfuric-acid"> <!--정의-->
    H<sub>2</sub>SO<sub>4</sub>
  </dfn>

  <!-- sup -->
  <p>각주<sup><a href="#footnote-1">[1]</a></sup></p>

  <!-- mark -->
  <mark>삼각함수</mark>

  <!-- time -->
  <time datetime="2018-02-22">Feb 22. 2018</time>
  <time datetime="2017-08-14T10:18">2017.08.14 10:18</time>

  <!-- abbr -->
  <abbr title="맥도날드">맥날</abbr>

  <!-- s -->
  <s>11,900원</s> <em>50%</em> 5,900원
```

#### [그룹핑 요소]
- `<address>`
  - href="tel:" - 전화 연결
- `<pre>` Preserved Text
  - 이메일, 빈 줄이 표시된 단락, 글 머리표가 붙은 줄로 표시된 목록 등에 사용
  - 컴퓨터 코드(언어) 표시 목적으로 사용
  - ASCII 아트 표시
  - 컴퓨터 코드, 출력, 키보드 블록을 나타내기 위해 pre 요소는 `<code>`, `<samp>`, `<kbd>` 요소와 함께 사용 가능
  <pre>
    아스키(ASCII) 코드

    ( *^-^)ρ(*╯^╰)
    ( •̀ ω •́ )y（。＾▽＾）
  </pre>

#### [임베디드 요소]
##### ▷ picture 요소
- 0개 이상의 `<source>` 요소와 **1개 이상의 img** 를 포함하는 컨테이너 요소.
- 다양한 스크린 환경에 맞는 적합한 이미지를 제공하기 위한 목적으로 사용.
- source 요소를 사용할 수 없을 경우, img 요소가 화면에 표시.
  ```html
    <picture>
      <source srcset="bamboo-pen2.png" media="(min-width: 900px)">
      <source srcset="bamboo-pen.png" media="(min-width: 600px)">
      <img src="bamboo-pen-narrow.png" alt="Bamboo Pen">
    </picture>

    <picture>
      <source srcset="bamboo-pen.svg" type="image/svg+xml">
      <img src="bamboo-pen-narrow.png" alt="Bamboo Pen">
    </picture>
  ```
##### ▷ source 요소
- picture, audio, video 요소의 다중 미디어 리소스를 지정하기 위해 사용.

##### ▷ video 요소
- 동영상 콘텐츠를 HTML 문서에 포함하기 위해서 사용.
- src 속성이나 `<source>` 요소을 이용해 여러 개의 동영상 소스 중 하나를 표시.(현재는 mp3,mp4등의 브라우저 지원으로 source 사용 X)
- 속성) `src` 파일 경로 / `poster` 포스터 이미지 경로 / `preload` 미리 읽어와서 사용자 경험 향상(메타데이터 / 비디오 다운로드)에 관한 설정 [none, metadata, auto(기본값)] `controls` 재생 컨트롤 표시 설정 / `autoplay` 자동 재생 설정(사용자 경험를 위해 자동 재생 설정은 가급적 사용 X) / `loop` 반복 설정 / `muted` 음소거 설정   

```html
  <video src="videofile.mp4" poster="posterimage.jpg" controls loop="true" autoplay="true" mute="true"><!--true값 생략 가능-->
    HTML5 <code>video</code> 요소를 지원하지 않는 구형 웹 브라우저를 사용 중입니다.
    <a href="http://outdatedbrowser.com/ko">최신형 브라우저로 업데이트</a> 하세요.
  </video>
```

##### ▷ audio 요소
- 오디오 콘텐츠를 포함하기 위해서 사용. video와 유사.
- 속성) `volume` 볼륨 조절(0.0 ~ 1.0)

```html
  <audio src="audiofile.mp3" controls>
    HTML5 <code>audio</code> 요소를 지원하지 않는 구형 웹 브라우저를 사용 중입니다.
    <a href="http://outdatedbrowser.com/ko">최신형 브라우저로 업데이트</a> 하세요.
  </audio>
```


##### ▷ track 요소
- 비디오/오디오 재생 시, 자막을 표시.
- `default` 속성을 설정하지 않을 경우, 자막 사용 안함 됨
```html
  <video src="videofile.mp4" poster="posterimage.jpg">
    <track kind="subtitles" src="videofile.ko.vtt" srclang="ko" label="한국어" default>
    <track kind="subtitles" src="videofile.en.vtt" srclang="en" label="English">
    <track kind="subtitles" src="videofile.en.vtt" srclang="ja" label="日本語">
  </video>

  <audio src="audiofile.mp3">
    <track kind="subtitles" src="audiofile.ko.vtt" srclang="ko" label="한국어">
    <track kind="subtitles" src="audiofile.en.vtt" srclang="en" label="English">
  </audio>
```

##### ▷ iframe 요소
- 인라인 프레임(Inline Frame)에 다른 HTML 페이지를 포함하여 화면에 표시.
- 속성) `allowfullscreen` : 프레임 전체화면 설정
  ```html
    <iframe
      width="560"
      height="315"
      src="https://www.youtube.com/embed/0wlXaHmmOVc?rel=0&amp;showinfo=0"
      style="border:0"
      allowfullscreen></iframe>
  ```

##### ▷ map 요소
- 이미지 맵(클릭 가능한 링크 영역)을 정의하기 위해 <area>와 함께 사용됨.
- [image-map.net](https://www.image-map.net/) : 이미지 맵 좌표 생성

##### ▷ area 요소
- 이미지의 핫스팟 지역 정의, 하이퍼링크 설정. <map> 내부에서만 사용 가능.
- 속성) `shape` 핫스팟 모양 설정 / `coords` 모양의 좌표 값 설정 / `href` 하이퍼링크 주소 설정 / `target` 새 창(탭) 열림 설정 / `alt` 대체 텍스트 설정 / `hreflang` 연결된 페이지의 언어 속성 설정 / ` download` canvas 데이터 다운로드 설정 / `title` 툴팁제공을 위해 사용   

```html
  <img src="products-map.jpg" alt="제품 모음" usemap="#products-map">
  <map name="products-map">
    <area
      shape="circle"
      coords="200,250,25"
      hreflang="en-GB"
      href="another.html"
      alt="Another Page"
      target="_blank"
      title="제품1">
  </map>
```

##### ▷ svg 요소
- 확장가능한 벡터 그래픽(SVG - Scalable Vector Graphics)은 2차원의 벡터 그래픽을 기술하기 위한 XML 마크업 언어.
  ```html
    <img src="svgfile.svg" alt="SVG File">

    <svg width="150" height="150" viewBox="0 0 150 150">
      <circle r="50" cx="75" cy="75" fill="#333" stroke="#900" stroke-width="4" />
    </svg>
  ```

</div>
</details>


---------------------------------------
<details open>
<summary>4일차 학습</summary>
<div markdown="4">

#### [테이블 요소]
- `<table>` 행(row),열(column) 및 셀(cell)을 포함
  - 복잡한 내용을 x, y 축에 따라 이해하기 쉽게 데이터를 구조화하는데 테이블을 사용.
  - 테이블 내 테이블을 중첩X
  - 테이블을 레이아웃(배치) 목적으로 사용해서는 안된다.
  - `border` 속성을 사용하여 테두리를 그리기 보다 CSS로 표현하기.   

- `<caption>` 테이블의 제목을 명시적으로 제공.
  - **[설명(summary)을 추가하는 방법]**
    - 테이블 내용이 복잡해 설명이 필요할 경우
      1. `aria-describedby` 속성을 사용해 설명 단락(paragraph)을 연결   

        ```html
          <p id="compare-shoes-table">국제(한국, 미국, 영국, 유럽) 성인 남성 운동화 사이즈 비교 표로 4행 12열로 구성되어 있습니다.</p>
          <table border='1' aria-describedby="compare-shoes-table">
          <!-- aria-describedby : 표에 대한 자세한 내용기술 / id값으로 연결-->
          <caption>성인 남성 운동화 사이즈표</caption>
            ...
          </table>
        ```   

      2. `<figure>` 요소에 `aria-labelledby` 속성을 사용해 제목(caption)을 연결    

        ```html
          <figure aria-labelledby="caption">
            <p>...</p>
            <table>
              <caption id="caption">...</caption>
              ...
            </table>
        ```  

- `<tr>` (table row) 테이블 행
  - `<th>` (table header) 셀 제목   

    ```
      [속성]
      scope : 행(row) 또는 열(col), 행그룹(rowgroup), 열그룹(colgroup)의 제목임을 명시
      abbr : 제목이 길어 축약(Abbreviation)이 필요할 때 사용
      colspan : 열 병합. 열(column)을 그룹 지을 때 사용
      rowspan : 행 병합. 행(row)을 그룹 지을 때 사용
    ```   

  - `<td>` (table data) 셀 내용 포함.   

    ```
      [속성]
      colspan : 열 병합. 열(column)을 그룹 지을 때 사용
      rowspan : 행 병합. 행(row)을 그룹 지을 때 사용
      headers : 셀 제목을 하나 이상 연결하여 읽기 용이하도록 구성할 때 사용
    ```   

- `<thead>`
  - 테이블 행 블록(row block) 내에 제목 열 그룹(column headers)으로 구성할 경우 사용. 선택적 사용(필수X)   

- `<tbody>`
  - 행 블록 내에 테이블 데이터로 구성할 때 사용. 선택적 사용(필수X), 명시적으로 사용해도 되고, 브라우저가 자동으로 만들어 줌.  

- `<tfoot>`
  - 행 블록 내에 열 요약(column summaries)로 구성할 때 사용. 선택적 사용(필수X)   

- `<col>`
  - 테이블 열을 하나 이상 묶고자 할 때 사용한다. 일반적으로 `colgroup` 요소 내부에 포함시킨다. 선택적 사용(필수X)   
  - 속성) `span` : 열 묶음 개수 설정  

- `<colgroup>`
  - 테이블 열 그룹을 만들고자 할때 사용한다. 내부에 `col` 요소를 포함하거나, 포함하지 않을 수 있다. 선택적 사용(필수X)
  - 속성) `span` : 열 묶음 개수 설정   

- [table](https://github.com/dreamfulbud/TIL/blob/master/ex/tabular.html) : 테이블 실습

#### [폼 요소]
- `<form>`
  - 폼은 텍스트필드, 버튼, 체크박스와 같은 폼 컨트롤을 포함하는 웹 페이지의 컴포넌트를 말함.
  - 사용자와 인터랙션을 수행한 결과(예: 검색)를 서버로 보낼 수 있다.
  ```html
    <form action="https://formspree.io/your@email.com" method="POST">
      ...
    </form>
  ```    

  - **method**
    ```
     GET  : 브라우저 주소 창에 정보가 남음. 기본값.
     POST : 브라우저 주소 창에 정보를 남기지 않음.
            개인정보등의 민감한 정보가 있을 겅우 사용. 파일(예: jpg, mp4 등)을 서버로 업로드할 때 사용.
    ```   

- `<input>`
  - 사용자의 데이터를 입력 받을 수 있는 폼 컨트롤을 말함.
  - 다양한 유형(Type) 설정이 가능하며, 유형에 맞는 역할을 수행한다.   
  - 속성) `name` / `placeholder` / `value` / `readonly` / `required` / `disabled` / `minlength` / `maxlength` / `list`
  - ※ `readonly` 속성이 설정된 값(value)은 전송되지만, `disabled` 속성이 설정된 값은 전송되지 않음.

  - file 사용 시 form에 `method="POST" enctype="multipart-formdata"`를 넣어야함
  ```html
  <form action="https://formspree.io/dreamfulbud@naver.com" method="POST" enctype="multipart-formdata">
    <input type="file" name="user_data_upload" id="user_data_upload">
  </form>
  ```

- `<label>`
  - 컨트롤에 레이블(이름)을 붙이고자 할 경우 사용.   

- `<button>`
  - 버튼 폼 컨트롤로 사용자의 인터랙션을 받아 액션을 트리깅(방아쇠) 처리함.   
  - type) `submit` / `button` / `reset`

- `<select>`
  - 드롭 다운 메뉴(옵션을 선택 할 수 있는) 컨트롤을 말함.
  - 내부에 `<option>` 요소를 포함하여 사용자에게 선택할 수 있도록 한다.
  - `<option>`을 묶어 그룹으로 만들고자 한다면 `<optgroup>` 요소를 사용하고, label 속성을 사용해 그룹 이름을 설정한다.
  - 속성) `name` / `multiple` 다중선택가능 / `disabled` / `required` / `size`   

    ```html
      <select name="user_hobby2" id="user_hobby2" multiple size="2">
      <!--multiple : 다중선택가능 / size : 2줄보임-->
    ```


- `<option>`  
  - `<select>`, `<datalist>`, `<optgroup>` 내부에 포함 가능한 컨트롤로 항목을 만드는데 사용됨.
  - 속성) `value` / `selected` / `label` / `disabled`   

- `<optgroup>`
  - `<option>` 컨트를을 그룹지을 때 사용됨.   
  - 속성) `disabled` / `label`

- `<textarea>`
  - 멀티라인 일반 텍스트 편집 컨트롤을 말한다.   
  - 속성) `name` / `placeholder` / `rows`(높이) / `cols`(폭) / `readonly` / `required` / `disabled` / `minlength` / `maxlength`  

  ```html
    <textarea name="user_comments" id="user_comments" cols="24" rows="5" style="resize:none;">
      남기고 싶은 말을 작성해주세요.
    </textarea>
  ```

- `<fieldset>`
  - 멀티라인 일반 텍스트 편집 컨트롤을 말한다.   

- `<legend>`
  - `<fieldset>` 컨트롤의 레이블(이름)을 설정하는 컨트롤.   

  ```html
    <fieldset name="user_acount">
      <legend>사용자 계정</legend>
      ...
    </fieldset>
  ```

- `<output>`
  - 계산된 결과를 출력하는 컨트롤.   
  ```html
    <form oninput="result_sum.value = parseInt(n1.value + n2.value, 10)">
      <p>
        <input type="number" name="n1" value="4"> +
        <input type="number" name="n2" value="10"> =
        <output name="result_sum">14</output>
      </p>
    </form>
  ```
- `<datalist>`
  - 데이터 목록 요소 컨테이너 컨트롤. 내부에 `<option>` 요소를 사용해 항목을 만든다.   

- `<progress>`
  - 작업의 완료 **진행 상황** 을 표시하는데 사용되는 컨트롤.   
  - 속성) `value` / `max`   

  ```html
    <progress value="10" max="100">10%</progress>
    <progress value="90" max="100">10%</progress>
  ```   

- `<meter>`
  - 알려진 범위 내에서의 **스칼라 측정** 또는 **분포 비율** 을 나타내는 컨트롤. (**게이지(gauge)** 라고도 불림)
  - 디스크 사용 현황, 쿼리 결과의 관련성, 특정 후보에 대한 투표율 등이 해당됨.
  - 속성) `value` / `min` / `max` / `low` / `high` / `optimum`   

  ```html
    <meter value="20" min="5" max="40">20</meter>
  ```
- [form](https://github.com/dreamfulbud/TIL/blob/master/ex/form.html) : 폼요소 실습 및 정리

</div>
</details>

---------------------------------------
<details open>
<summary>5일차 학습</summary>
<div markdown="1">

#### [인터랙티브 요소]
##### ▷ `<details open>` 요소
- 디스클로저 위젯(disclosure widget, 참고: https://goo.gl/uznvFY)으로 정보를 감추거나, 펼쳐서 보여준다.
- 모든 정보를 일시에 공개하지 않고 사용자의 요구에 맞춰 정보를 공개할 수 있다. (화면의 복잡함을 줄임)
- 아코디언(Accordion) 컴포넌트와 비슷하게 작동한다.
- 참고로 각주(footnote)에는 적합하지 않다.
- 속성) `open` - 페이지 로딩 시, 위젯을 펼쳐 표시하도록 설정

  ```html
    <details open>
      ...
    </details>
  ```

##### ▷ `<summary>` 요소
- `<details open>` 요소의 레이블/캡션(제목), 서머리(요약) 등을 표시한다.
- 폼 `<fieldset>` 요소의 제목을 `<legend>`가 표시하듯 비슷하다.

  ```html
    <section class="progress window">
      <h1>"Really Achieving Your Childhood Dreams" 파일 복사</h1>
      <details open>
      <summary>복사중... <progress max="375505392" value="97543282"></progress> 25%</summary>
      <dl>
        <dt>초당 전송 속도:</dt>
        <dd>452KB/s</dd>
        <dt>로컬 파일이름:</dt>
        <dd>/home/rpausch/raycd.m4v</dd>
        <dt>원격 파일이름:</dt>
        <dd>/var/www/lectures/raycd.m4v</dd>
        <dt>재생시간:</dt>
        <dd>01:16:27</dd>
        <dt>컬러 프로파일:</dt>
        <dd>SD (6-1-6)</dd>
        <dt>영상 크기(너비×높이):</dt>
        <dd>640×480</dd>
      </dl>
      </details>
    </section>
  ```
##### ▷ `<dialog>` 요소
- 다이얼로그(Dialog, 참고: https://goo.gl/pQ7gSX)는 사용자의 결정 또는 정보 입력을 요구하는 컴포넌트를 말함.
- '모달 윈도우' 또는 '대화상자'로도 불린다.(레이어팝업)
- 속성) `open` - 페이지 로딩 시, 위젯을 표시하도록 설정   

  ```html
    <dialog open>
      ...
    </dialog>
  ```
- [인터랙티브 요소](https://github.com/dreamfulbud/TIL/blob/master/ex/interactive.html) : 실습


#### [스크립팅 요소들]
##### ▷ `<script>` 요소
- 속성) `src` / `type` html5부터는 type 생략 가능 / `async` / `defer`

##### ▷ `<noscript>` 요소
- 사용자의 웹 브라우저 환경에서 스크립트를 지원되지 않거나, 스크립트가 꺼져있는 경우, 문서에 표시될 문구를 삽입한다.

##### ▷ `<canvas>` 요소
- JavaScript를 사용하여 그래픽(비트맵)을 그릴 때 사용한다.
- `<canvas>` 요소로부터 2D 또는 WebGL 컨텍스트 객체를 추출해 그래픽을 그릴 수 있다.

#### [유저 인터랙션 속성]
##### ▷ `hidden` 속성
- 모든 HTML 요소들은 hidden 속성을 가질 수 있으며, 요소에 설정되면 요소가 아직 페이지의 현재 상태와 직접적으로 관련이 없거나 페이지의 다른 부분에서 내용을 재사용하도록 선언하는 데 사용된다. 브라우저는 hidden 속성이 설정된 요소를 화면에 렌더링하지 않는다.

##### ▷ `tabindex` 속성
  - 요소를 키보드로 탐색할 수 있도록 설정하거나, 제외 또는 순서대로 탐색할 수 있도록 설정할 수 있다.
  - "탭(Tab) 이동"이란 용어는 순차적 포커스 탐색을 사용하여 포커스 가능(Focusable) 요소 사이를 이동하는 것을 의미한다.
  - **[기본적으로 포커스 가능한 요소들]** (참고: https://allyjs.io/data-tables/focusable.html)
    - 폼 컨트롤 요소들           : input, button, textarea, select 등
    - href 속성을 가진 요소들     : a, area
    - controls 속성을 가진 요소들 : video, audio
  - 마우스에만 의존X, 웹접근성을 고려하여 마우스, 키보드 둘다 고려할것.

    ```
      - [양수] 논리적 포커스 흐름에 방해가 되기에 사용을 권장하지 않음
      - [0] div 요소는 포커스를 가지지 않는 요소이지만, 포커스를 적용할 수 있게 된다.
        - 컴포넌트 제작 시, 비 포커스 요소에 포커스를 적용해야 할 경우 유용하게 사용됨.
      - [-1] 일반적인 포커스 순서에서 제외시킬 수 있다.(JavaScript 프로그래밍으로 포커스 처리 가능)
        - 컴포넌트의 일부 요소를 일시적으로 포커스 순서에서 제외한 후, 목표에 따라 포커스를 다시 활성화 처리할 수 있다.
    ```

##### ▷ `accesskey` 속성
- 모든 HTML 요소는 accesskey 속성을 가질 수있다. 속성 값은 키보드 단축키로 설정된다.
- 하지만 accesskey 속성의 단축키는 브라우저와 운영체제 플랫폼에 의존하고 있어 운영체제마다 사용자 경험이 달라진다.
- 쉽게 말해 Windows 사용자와 Mac OSX 사용자가 사용하는 단축키는 달라진다. (iPhone과 Android 사용자 경험이 다른 것처럼)
  ```
    [브라우저 × 운영체제 플랫폼]
    Windows
      Chrome  : Alt + 단축키
      IE      : Alt + 단축키
      Safari  : Alt + 단축키
      Opera   : Alt + 단축키
      Firefox : Alt + Shift + 단축키
    Mac OSX
      Chrome  : Control + Alt + 단축키
      Safari  : Control + Alt + 단축키
      Opera   : Control + Alt + 단축키
      Firefox : Control + 단축키
    Linux
      Chrome  : Alt + 단축키
      Opera   : Alt + 단축키
      Firefox : Alt + Shift + 단축키
  ```
  ```html
    [사용 예시]
      <button
        type="button"
        class="button is-collect"
        accesskey="C"
        onclick="collect()">
        수집
      </button>
  ```

##### ▷ `contenteditable` 속성
- contenteditable 속성이 설정된 요소는 사용자가 직접 편집할 수 있도록 만들어 준다.
- 값이 true 또는 빈 문자열("")일 경우 편집 허용.
- 값이 false 일 경우 편집을 허용하지 않음.
- **위젯기능** 에 응용 가능.
  ```html
    <p contenteditable>
      ...
    </p>
  ```

##### ▷ `draggable` 속성
- 모든 HTML 요소는 draggable 속성을 가질 수 있다.
- 값이 true 일 경우 드래그(Drag) 가능.
- 값이 false 또는 빈 문자열("")일 경우 드래그 불가능.
```html
  <p draggable="true">
    ...
  </p>
```
- 마우스에 의존하기때문에 위험할 수 있음.

#### [문서 메타데이터 요소들]

##### ▷ `<head>` 요소
- 문서의 제목과 스타일시트, 스크립트 링크 또는 선언을 포함하는 문서의 일반적인 정보(메타데이터)를 제공한다.
  대부분 브라우저는 마크업에서 <head> 요소가 생략될 경우, 자동으로 <head> 요소를 생성하지만 일부는 그렇지 않다.
- [자동으로 <head> 요소를 생성하지 않는 브라우저 환경]
  - Android <= 1.6 / iPhone  <= 3.1.3 /  Opera   <= 9.27 / Safari  <= 3.2.1. / Nokia 90

##### ▷ `<title>` 요소
- 브라우저의 타이틀 바(Title Bar)나 페이지 탭에 보여지는 문서의 제목을 정의.
- 텍스트만 포함할 수 있으며 포함된 태그들은 해석되지 않음.

##### ▷ `<meta>` 요소
- 다른 메타 요소들(title, base, link, style)로 나타낼 수 없는 메타데이터를 정의할 때 사용.
- [메타데이터의 종류]
  - **charset이 설정된 경우:**
    - charset 선언. 즉 웹페이지를 작성하는 일련의 형식에 사용되는 문자 인코딩(charset)에 대한 설정.
    - 이 속성보다 요소의 lang 속성이 우선하여 적용됨. (즉, 덮어쓰기 됨. 예: div lang="fr")
  - **http-equiv 속성이 설정된 경우:**
    - pragma 지시어(Directive)로 일반적으로 웹서버가 제공하는 웹페이지가 어떻게 제공되어야 하는지에 대한 정보를 제공.
    ```html
      [예시]
        ✤ HTML 5에서는 더 이상 아래와 같이 사용되길 권장하지 않음.
          <meta http-equiv="Content-Type" content="text/html;charset=UTF-8">
        ✤ 3초 뒤에 url 값에 설정된 페이지로 이동하게 됨.
          <meta http-equiv="refresh" content="3;url=https://google.com">
    ```
  - **name 속성이 설정된 경우:**
    - 문서 수준 메타 데이터의 이름을 정의하며, content 속성 값을 통해 설정.

- [속성]
  - charset
  - http-equiv
  - content
      이 속성은 컨텍스트에 따라 http-equiv또는 name속성 과 연결된 값을 제공.
  - name
    - application name:
      - 웹 페이지에서 실행중인 웹 애플리케이션 이름 정의.
      - 간단한 웹 페이지는 application-name 메타를 정의해서는 안됨.
    - description : 페이지의 내용에 대한 짧고 정확한 요약을 설정.
    - keywords : 쉼표로 구분된 문자열로 페이지의 내용과 관련된 키워드를 설정.
    - author : 문서 작성자의 이름을 정의.
      ```html
        <meta name="description" content="웹페이지 내용을 요약해서 기술">
        <meta name="keywords" content="웹페이지에 주요 키워드를 콤마(,)로 구분하여 작성. ">
        <meta name="author" content="웹페이지 제작자">
      ```
    - robots
      - 검색 로봇이 웹 페이지를 크롤링하는 동작에 대한 정의.
        - index / noindex : 로봇이 페이지를 색인하는 것을 허용/금지
        - follow / nofollow : 로봇이 페이지의 링크를 따라가는 것을 허용/금지
        - noarchive : 검색 엔진이 페이지의 컨텐츠를 캐싱하는 것을 막음
        - nosnippet
        - noimageindex
          ```html
            <meta name="robots" content="index">
          ```
    - viewport
      - (비표준) 초기 viewport 크기 설정에 관한 힌트를 제공.
      - 이 속성은 몇 개의 모바일 디바이스에 의해서만 사용됨.
       - **width** / height / **initial-scale** / maximum-scale / minimum-scale / user-scalable
        ```html
          <meta name="viewport" content="width=device-width, initial-scale=1">
      ```

##### ▷ `<link>` 요소
- 현재 문서와 외부 리소스와의 관계(relation)를 명시.
- 이 요소는 스타일시트를 링크 하는데 가장 많이 사용됨.
- [속성]
  - rel      : 문서와의 관계 명시.
  - type     : 링크된 리소스 MIME 타입 정의. (기본 적용: text/css)
  - href     : 링크된 리소스 URL 설정.
  - hreflang : 링크된 리소스의 언어 설정.
  - media    : 링크된 리소스가 적용될 미디어(media)를 설정. all, screen, print
  ```html
  기본 스타일시트 설정
    <link href="style.css" rel="stylesheet">

  대체 스타일시트 설정: View > Page Style 메뉴에서 사용할 스타일시트를 고를 수 있다. (Chrome은 해당 X)
    <link href="default.css" rel="stylesheet" title="기본 스타일">
    <link href="fancy.css" rel="alternate stylesheet" title="팬시">
    <link href="basic.css" rel="alternate stylesheet" title="베이직">
  ```

##### ▷ `<style>` 요소
- 문서나 문서 일부에 대한 스타일 정보를 포함.기본적으로 CSS 언어가 사용됨.
- [속성] type(HTML5 생략가능) / media / scoped (해당영역 내에만 적용. 현재 제대로 지원하는 브라우저 없음.) / title / disabled
  ```html
    <style>
      body {
        color: #323232;
      }
    </style>

    <section>
      <style scoped>
        p { color: #902c1f; }
      </style>
      <p> ... </p>
    </section>
  ```

##### ▷ `<base>` 요소
  - 문서에 포함된 모든 상대 URL들의 기준 URL을 나타냄.
  - **한 문서에 하나** 의 <base> 요소만 존재해야 함.
    ```html
    <base target="_blank" href="http://www.example.com/">
    ```


</div>
</details>
