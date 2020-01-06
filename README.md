# Wemade Service HTML Convention
HTML Coding Convention

## 목차

1. [Doctype 선언](#Doctype-선언)
1. [기본언어 설정](#기본언어-설정)
1. [들여쓰기](#들여쓰기)
1. [큰따옴표 사용](#큰따옴표-사용)
1. [소문자 사용](#소문자-사용)
1. [단일 태그](#단일-태그)
1. [Custom 어트리뷰트](#Custom-어트리뷰트)
1. [Type 지정](#Type-지정)
1. [Boolean 어트리뷰트](#Boolean-어트리뷰트)
1. [엔티티 참조](#엔티티-참조)
1. [Meta 태그](#Meta-태그)
    - [캐릭터셋 정의](#캐릭터셋-정의)
    - [IE호환 모드](#IE호환-모드)
    - [오픈그래프 프로토콜](#오픈그래프-프로토콜)
1. [마크업](#마크업)
    - [시멘틱 마크업](#시멘틱-마크업)
    - [간결한 마크업](#간결한-마크업)
<!-- 1. [두치](#terminology)
    - [두치111](#두치111)
    - [두치222](#두치222)
    - [두치333](#두치333) -->



## Doctype 선언
DHTML, XHTML등 레거시 선언 코드는 사용하지 않는다.
```html
<!DOCTYPE html>
<html>
...
</html>
```


## 기본언어 설정
`lang` 어트리뷰트를 적용해 문서의 기본언어를 설정한다. [국가별 코드 목록](http://www.lingoes.net/en/translator/langcode.htm)
```html
<html lang="ko">
...
</html>
```


## 들여쓰기
HTML파일의 Indent는 공백(space)으로 간격은 2개로 지정한다.
```html
<!-- NO -->
<ul>
    <li>
        <a href="#menu1">메뉴1</a>
        <a href="#menu2">메뉴2</a>
    </li>
</ul>

<!-- YES -->
<ul>
  <li>
    <a href="#menu1">메뉴1</a>
    <a href="#menu2">메뉴2</a>
  </li>
</ul>
```

`<head>, <body>` 코드는 들여쓰기 하지 않는다.
```html
<!-- NO -->
<html lang="ko">
  <head>
    <meta charset="utf-8">
    <meta name="locale" content="kr">
  </head>
  <body>
  ...
  </body>
</html>

<!-- YES -->
<html lang="ko">
<head>
<meta charset="utf-8">
<meta name="locale" content="kr">
</head>
<body>
...
</body>
</html>
```


## 큰따옴표 사용
어트리뷰트 값은 반드시 큰따옴표("")로 감싼다.
```html
<!-- NO -->
<button type='submit' class='btn_submit'>검색</button>

<!-- YES -->
<button type="submit" class="btn_submit">검색</button>
```


## 소문자 사용
태그, 어트리뷰트 이름은 반드시 소문자를 사용한다.
```html
<!-- NO -->
<BUTTON Type='submit' class='btn_submit'>검색</BUTTON>Type
<!-- YES -->
<button type='submit' class='btn_submit'>검색</button>
```


## 단일 태그
아래 단일 태그들은 끝 부분에 슬래시(/) 없이 사용한다.  
`area, base, br, col, command, embed, hr, img, input, keygen, link, meta, param, source, track, wbr`

```html
<!-- NO -->
<img src="/img/table.png" alt="매출표" />
<hr />
<input type="text" name="id" placeholder="아이디를 입력하세요." />

<!-- YES -->
<img src="/img/table.png" alt="매출표">
<hr>
<input type="text" name="id" placeholder="아이디를 입력하세요.">
```


## Custom 어트리뷰트
`data-*, aria-*` 어트리뷰트 네이밍은 kebab-case를 적용한다.
```html
<!-- NO -->
<input type="text" name="first" placeholder="입력" aria-field_required="false">

<!-- YES -->
<input type="text" name="first" placeholder="입력" aria-field-required="false">
```
`data-*, aria-*` 어트리뷰트이 여러개일 경우 끝부분에 선언하며 개행한다.
```html
<!-- NO -->
<input type="text" aria-labelledby="tp1-label" aria-describedby="tp1" aria-required="false" name="first" placeholder="입력">

<!-- YES -->
<input type="text" name="first" placeholder="입력" 
  aria-labelledby="tp1-label"
  aria-describedby="tp1"
  aria-required="false">
```


## Type 지정
`<input>, <button>` 태그 사용시 반드시 `type`을 지정한다.
```html
<!-- NO -->
<input name="keyword" maxlength="20" placeholder="입력하세요">
<button class="btn_submit">검색</button>

<!-- YES -->
<input type="text" name="keyword" maxlength="20" placeholder="입력하세요">
<button type="submit" class="btn_submit">검색</button>
```
`<link>, <script>` 에서 CSS, JS파일을 불러올 때 `type`을 생략한다.
```html
<!-- NO -->
<link rel="stylesheet" type="text/css" href="/css/desktop/main.css" />
<script type="text/javascript" src="/js/desktop/app.js"></script>

<!-- YES -->
<link rel="stylesheet" href="/css/desktop/main.css">
<script src="/js/desktop/app.js"></script>
```


## Boolean 어트리뷰트
`required, readonly, checked, disabled, selected`   
해당 어트리뷰트는 값을 적용하지 않고 사용하며 가급적 끝부분에 선언한다.
```html
<!-- NO -->
<input type="text" name="school" required="required">
<input type="number" name="phone" readonly="readonly">
<input type="checkbox" value="미르4" checked="checked">
<textarea cols="20" disabled="disabled"></textarea>
<option value="2019" selected="selected">2019</option>

<!-- YES -->
<input type="text" name="school" required>
<input type="number" name="phone" readonly>
<input type="checkbox" value="미르4" checked>
<textarea cols="20" disabled></textarea>
<option value="2019" selected>2019</option>
```


## 엔티티 참조
[엔티티 참조](https://dev.w3.org/html5/html-author/charref)는 사용하지 않는다. (단 `<, >, &` 는 예외)
```html
<!-- NO -->
<p class="copyright">&copy; Wemade Co., Ltd. All rights reserved.</p>

<!-- YES -->
<p class="copyright">ⓒ Wemade Co., Ltd. All rights reserved.</p>
```

## Meta 태그
* 캐릭터셋 정의
* IE호환 모드
* 오픈그래프 프로토콜


### 캐릭터셋 정의
UTF-8은 모든 유니코드 문자를 표현할 수 있으며 한글, 알파벳, 한자등을 다루어야 하기 때문에 적합하다.
```html
<head>
<meta charset="utf-8">
</head>
```

### IE호환 모드
IE호환 모드는 Desktop Web에서만 사용한다.
```html
<head>
<meta http-equiv="x-ua-compatible" content="ie=edge">
</head>
```

### 오픈그래프 프로토콜
자세한 내용은 [링크](https://ogp.me/)를 참조한다.
```html
<!-- Open Graph Protocol -->
<meta property="og:title" content="위메이드, 中 저작권 침해 소송 승소"> 
<meta property="og:type" content="article"> 
<meta property="og:url" content="https://news.v.daum.net/v/20200102144513103"> 
<meta property="og:image" content="https://img1.daumcdn.net/thumb/S1200x630/?fname=https://t1.daumcdn.net/news/202001/02/mk/20200102144514749xcia.jpg"> 
<meta property="og:description" content="위메이드(대표 장현국)가 중국에서 낸 '미르의 전설2' 저작권 침해 소송에서 잇따라 승소했다.">
```


## 마크업
마크업은 명확하고 간결해야 한다.
* 시멘틱 마크업
* 간결한 마크업

### 시멘틱 마크업
목적에 맞지 않는 태그 사용은 피해야한다. 
```html
<!-- NO -->
<div class="header">
  <p><em>애국가 1절</em><p>
  동해물과 백두산이 마르고 닳도록<br>
  하느님이 보우하사 우리나라 만세
</div>

<!-- YES -->
<header class="header">
  <h2>애국가 1절</h2>
  <p>동해물과 백두산이 마르고 닳도록</p>
  <p>하느님이 보우하사 우리나라 만세</p>
</header>

<!-- YES -->
<header class="header">
  <dl>
    <dt>애국가 1절</dt>
    <dd>
      <p>동해물과 백두산이 마르고 닳도록<br>하느님이 보우하사 우리나라 만세</p>
    </dd>
  </dl>
</header>
```

### 간결한 마크업
불필요한 태그를 추가할 이유는 없다. 마크업이 길어지면 그만큼 문서의 크기는 증가하고 렌더링 속도는 느려진다.
```html
<!-- NO -->
<span class="thumbnail">
  <img src="/img/thumbnail.jpg" alt="썸네일 이미지" />
</span>

<!-- YES -->
<img src="/img/thumbnail.jpg" class="thumbnail" alt="썸네일 이미지" />
```
