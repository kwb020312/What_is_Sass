# Sass

- ※ 해당 문서는 Sass의 <a href="https://sass-lang.com/documentation">공식 문서</a>를 보고 작성되었음을 미리 밝힙니다.

css적용이 웹페이지를 꾸며주는 화장이라고 본다면 최근의 사람들은 CSS보단 Sass 혹은 Scss에 열중하고있다. 해당 Repository에선 대체 해당 라이브러리들이 어떠한 장점을 갖고있는지에 대하여 알아보겠다.

<img src="gitImages\Sass_Logo.jpg">

<blockquote cite="https://sass-lang.com/documentation">
    <i>Sass는 CSS로 컴파일 된 스타일 시트 언어입니다. 완전히 CSS 호환 구문으로 변수 , 중첩 규칙 , 믹스 인 , 함수 등 을 사용할 수 있습니다 . Sass는 큰 스타일 시트를 잘 구성하고 프로젝트 내부와 프로젝트간에 디자인을 쉽게 공유 할 수 있도록합니다.</i>
</blockquote>

공식 홈페이지에선 Sass에 대하여 이렇게 소개하고있다.

CSS로 컴파일 된 스타일 시트 언어,
CSS내에서 변수, 함수, 믹스인, 중첩 규칙 사용가능

짧게 줄여 해당 두가지가 가장 큰 장점이라 볼 수 있다.

## 주석처리

Sass에서도 다른 프로그래밍 언어와 같이 // 와 같은 한줄주석, /\* \*/ 와 같은 여러 줄 주석이 가능하다.

## 들여쓰기

```css
p .sans
    font: Helvetica, sans-serif
```

css와는 달리 위 문법처럼 들여쓰기로도 스타일 적용이 가능하다

## 함수 및 변수사용

```css
@function pow($a, $b) $sum: $a + $b @return $sum;
```

위와같이 예약어 에는 @ 를 붙이고 선언할 인자 혹은 변수에는 $ 표시를 붙여 css안에서도 자연스럽게 변수 및 반복문 혹은 함수 조건문 사용이 가능하다

## Scss VS Sass

두 구문의 차이는 큰 차이가 나진 않으나 <img src="gitImages\Sass.jpg">

위의 Sass문법에서 세미콜론 과 중괄호 와 같은 기존 CSS문법을 따라간것이 Scss이다.

<img src="gitImages\Scss.jpg">

## url처리

기존의 css는 url을 직접 넣어주어야 했는데, Sass의 경우 변수로 선언하여 할당해줄 수 있다.

```css
$test_url: 'http://~~'

@font
    src: url("#{$test_url}")
```

위에 보는것과 같이 #{ $변수 } 로 선언해야함

## 다양한 내장함수

기존의 calc() 와 같은 css내장함수 뿐만 아니라 @use 를 사용한다면 Sass의 매우 많은 내장함수를 사용할 수 있음

```css
@use "sass:math"

.test
    $width: 800px
    position:absolute
    /* math.div = divide 즉 나누기를 뜻함 */
    left: math.div($width,2);
```

이렇게 max() , min() 함수의 사용또한 가능함

- ※ 내장함수는 앞에 $ 를 붙이지 않는다.

<img src="gitImages\innerFunc.jpg">
