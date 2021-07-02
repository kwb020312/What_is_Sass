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

## 설치방법

```javascript
npm i -g sass
```

이제 sass파일을 생성 후

<img src="gitImages\Transfer_Sass.jpg">

아래와 같이 입력해주면 sass파일이 css파일로 변환된다.

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

## 내부중첩

Sass는 일일히 따로 중첩하지 않아도 상위태그 아래로 들여쓰여진 것들은 모두 상위태그를 가르키기 때문에

<img src="gitImages\Sass_Include.jpg">

위와 같이 입력하면

<img src="gitImages\CSS_Include.jpg">

이렇게 변환된다.

지금이야 별 차이가 없겠지만 문장이 길어진다면 매우 큰 차이가 있을 것 같다.

- CSS가 더 보기 좋은 것 같은데..

## 조건문

Sass에서의 조건문은 중괄호로 감싸지 않고 인자로 전달하여 처리하는데, 인자의 첫번째 요소는 조건, 두번쨰 요소는 조건이 참일때, 세 번쨰 요소는 조건이 거짓일 때를 나타낸다

<img src="gitImages\If.jpg">

위 사진은 Sass에서 조건이 참이라면 색이 붉어지고 아니면 파래지는데,

<img src="gitImages\if_css.jpg">

조건식이 false이기 때문에 color:blue가 되었다.

## 종속 스킵

margin-top, margin-bottom과 같이 한 속성에서 여러갈래로 하이픈(-) 처리하여 나뉘는 요소를 Sass에선 쉽게 처리할 수 있는데,

<img src="gitImages\-_attr_sass.jpg">

위와같이 입력해주면 css반환으론

<img src="gitImages\-_attr_css.jpg">

위와같이 반환된다.

## 부모선택자

Sass에서 부모를 선택하는 부모선택자는 & 를 사용하는데,

예를들어

```css
.test
    color: red

    &_2
        color: blue
```

를 변환하면 어떻게 될까??
&는 자신을 .test로 취급하고 .test_2라는 Class에 color:blue라는 스타일이 입혀질 것이다.

- ※ 주의 : Sass 속성 선택자(:) 뒤에는 반드시 공백이 필요하며 없을경우 오류를 발생시킴.

<img src="gitImages\&Parent.jpg">

위의 Sass파일을 CSS로 변환시 아래와 같아짐

<img src="gitImages\&Children.jpg">

## 글로벌 변수

Sass의 변수는 기본적으로 다른 Sass에서 긁어다 쓸 수 있는데 별도의 Exports 과정은 필요없고 원하는 Sass에서

```css
@use 'SassFileName';
```

선언을 하면 자연스럽게 mixin함수 혹은 변수를 사용할 수 있다.

예를 들어 test.sass에서 black을 선언한다면

<img src="gitImages\Export_Black.jpg">

이후 test2.sass에서 import해온다

<img src="gitImages\Import_Black.jpg">

이후 test2를 css로 변경해준다면,

<img src="gitImages\Export_Result.jpg">

```css
@use "sass:math"

// 아래와 같은 내장함수를 수정할 수 없음.
math.$pi: 0;
```

기본적으로 스타일 내부에서도 변수를 선언 및 변경이 가능한데, 기존의 자바스크립트 클로져 구조와 같은 구조를 갖는 전역, 지역 변수를 사용할 수 있다.

```css
$test: 123

body
    /* fontSize 123 */
    font-size: $test
    $test: 456
    /* fontSize 456 */
    font-size: $test
```

## @forward

forward함수는 모듈을 거쳐갈 수 있도록 도와주는 것이다.

```css
// Base.sass
$color: "black";
```

```css
// Forward.sass
@forward "Base";
```

```css
// Test.sass
@use "Forward" as *

body
    color: $color;
```

이러한 처리과정을 거치고 난 이후의 결과는 아래와 같다

<img src="gitImages\Forward_Func_Result.jpg">

## import

import 는 use함수와 매우 흡사하며 sass의 코드를 그대로 가져올 때 사용이 가능하다 예를들어

```css
/* base.sass */
body
    color:red;
```

```css
/* new.sass */
@import base;
```

를 하게되면 new.sass파일을 변환했을 때 아래와 같은 결과가 나온다.

<img src="gitImages\import_result.jpg">

## if

if 함수를 사용하는 방법은 mixin 혹은 function에서 볼 수 있다.

```sass
@mixin test($testVal:0)
    @if $testVal === 0
        color: red;
```

위와 같이 코딩한 후 변환시켜주면 아래와 같이 변환된다.

<img src="gitImages\Sass_If_Result.jpg">

## For

Sass에서 if뿐 아니라 for문 또한 사용이 가능하다

@for 변수 from 변수초기값 to 종료조건

```sass
@mixin test($val:0, $i:0)
    @for $i from 0 to 5
        body
            color: red

@include test()
```

해당 sass파일을 css로 변환하면 아래와 같이 변환된다.

<img src="gitImages\Sass_For.jpg">

## Extend

@extend 함수를 사용하면 자신이 이후에 지목한 셀렉터의 스타일을 그대로 가져온다.

예를 들어

```sass
/* test.sass */
body
    color: red

p
    @extend body
```

를 적어놓은 후 css파일로 변환시 아래와 같은 결과로 반횐된다.

<img src="gitImages\Extend_Body.jpg">

## @error

@mixin 혹은 @function 을 이용할 때 내가 예상하지 못했던 결과로 오류를 받지 않으려면 어떤식으로 대처해야할까?

@error 함수를 사용하면 된다.
해당 함수는 뒤에오는 문자열을 출력해주는 역할을 하는데 @if문을 걸어 특수한 상황에 출력해주는 편이 좋다.

```sass
@mixin test($a, $b)
    @if $a < $b
        @error "A Must Bigger Than B"

body
    @include test(1,2)
```

위와 같은 코딩을 하고 test의 인자로 a에 더 적은값을 입력한 후 css파일로 변환하면 콘솔에 아래와 같이 출력되며 변환이 취소된다.

<img src="gitImages\@error.jpg">

## @warn

@warn함수는 @error함수와 거의 비슷한 역할을 시행하지만 유일한 차이점은 경고를 할 뿐 sass파일의 반환을 중지시키지 않는다는 점이다.

```sass
@mixin test($a, $b)
    @if $a < $b
        @warn "A Must Bigger Than B"

body
    @include test(1,2)
```

위와같이 입력한 후 css파일로 변환시 변환이 되지만 콘솔에 아래와 같이 출력된다

- ※ <i>위 코드의 경우에는 덧씌울 css스타일이 없어서 공백임</i>

<img src="gitImages\@warn.jpg">

## @debug

디버그는 콘솔에 표시를하며 @warn함수와 매우 유사하다,

중요도로 따지자면 @error > @warn > @debug 순이라고 생각하면 편하다.

```sass
@mixin test($a, $b)
    @if $a < $b
        @debug "A Must Bigger Than B"

body
    @include test(1,2)
```

## @else & @else if

if문이 있다면 외의 경우를 포함하는 else와 else if 또한 사용하고 싶을 것이다 앞에 @ 기호를 붙여주면 if문과 같은 문법으로 사용이 가능하며

```sass
@mixin test()
    @if false
        color: red
    @else if true
        color: blue
    @else
        color: blue

body
    @include test()
```

위의 코드를 입력 시 아래와 같이 반환된다.

<img src="gitImages\@else.jpg">

## @each

JavaScript의 꽃은 객체배열 이라고 볼 수 있는데 배열은 어떻게 사용해야할까??

```css
$colors: 'red', 'orange', 'yellow'

@each $c in $colors
    .col_#{$c}
        color: $c
```

,로 구분하며 @each는 기존의 JS문법과 동일하다 기존의 문자열에 변수를 할당하고 싶을 때 에는 #{} 로 감싸주면 됨

<img src="gitImages\@each.jpg">

## @while

반복문으로 for문 뿐만이 아닌 while문 또한 사용이 가능하다.

```sass
@function test($a: 1, $b: 3)
    @while $a < $b
        $a: $a + 1
    @return $a+'px'

body
    font-size: test()
```

문법은 JS와 동일하기 때문에 그대로 사용하면 됨
