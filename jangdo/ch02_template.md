# 템플릿 문법

Vue.js는 렌더링 된 DOM을 Vue 인스턴스의 데이터에 선언적으로 바인딩 할 수 있는 HTML 기반 템플릿 구문을 사용한다.
모든 Vue.js 템플릿은 스펙을 호환하는 브라우저 및 HTML 파서로 구문 분석 할 수있는 유효한 HTML이다.

내부적으로 Vue는 템플릿을 가상 DOM 렌더링 함수로 컴파일 한다.
반응형 시스템과 결합된 Vue는 앱 상태가 변경 될 때 최소한으로 DOM을 조작하고 다시 적용할 수 있는 최소한의 컴포넌트를 지능적으로 파악할 수 있다.


## 보간법(Interpolation)

### 문자열
데이터 바인딩의 가장 기본 형태는  "Mustache" 구문(이중 중괄호)을 사용한 텍스트 보간이다.
<pre>
&lt;span&gt;메시지 : {{ msg }}&lt;/span&gt;
</pre>
Mustache 태그는 해당 데이터 객체의 msg 속성 값으로 대체 된다.또한 데이터 객체의 msg 속성이 변경될 때 마다 갱신된다.

### 원시 HTML
이중 중괄호(Mustache)는 HTML이 아닌 일반 텍스트로 데이터를 해석한다.
실제 HTML을 출력하려면 v-html 디렉티브를 사용해야 한다.
<pre>
&lt;div v-html="rawHtml"&gt;&lt;/div&gt;
</pre>

### 속성
Mustache는 HTML 속성으로 사용할 수 없으며 대신 v-bind 디렉티브를 사용해야 한다.
<pre>
&lt;div v-bind:id="dynamicId"&gt;&lt;/div&gt;
&lt;button v-bind:disabled="someDynamicCondition"&gt;&lt;/button&gt;
</pre>

### Javascript 표현식 사용하기
모든 데이터 바인딩 내에서 Javascript표현식의 모든 기능을 지원한다.
<pre>
{{ number + 1 }}
{{ ok ? 'YES' : 'NO' }}
{{ message.split('').reverse().join('') }}
&lt;div v-bind:id="'list-' + id"&gt;&lt;/div&gt;
</pre>
이 표현식은 Vue 인스턴스 데이터 범위 내에서 Javascript로 계산된다.
각 바인딩에 하나의 단일 표현식 만 포함될 수 있다.

## 디렉티브
v- 접두사가 있는 특수 속성이다.
디렉티브 속성 값은 <strong>단일 Javascript표현식</strong>이 된다.
디렉티브의 역할은 표현식의 값이 변경될 때 사이드이펙트를 반응적으로 DOM에 적용하는 것이다.

### 전달인자
일부 디렉티브는 콜론으로 표시되는 "전달인자"를 사용할 수 있다.
<pre>
&lt;a v-bind:href="url"&gt;&lt;/a&gt;
&lt;a v-on:click="doSomething"&gt;&lt;/a&gt;
</pre>

### 수식어
점으로 표시되는 특수 접미사로, 디렉티브를 특별한 방법으로 바인딩 해야 함을 나타낸다.

## 필터
Vue.js에서는 일반 텍스트 서식을 적용할 때 사용할 수 있는 필터를 정의할 수 있다.
Mustache 보간과 v-bind 표현식 두 곳에서 사용할 수 있다.
Javascript 표현식의 끝에 추가해야 하며 "파이프" 기호로 표시 된다.
<pre>
{{ message | capitalize }}
&lt;div v-bind:id="rawId | formatId"&gt;&lt;/div&gt;
</pre>

필터 함수는 항상 표현식의 값을 첫번째 전달 인자로 받는다.
<pre>
new Vue({
    // ...
    filters: {
        capitalize: function (value) {
            if (!value) return ''
            value = value.toString()
            return value.charAt(0).toUpperCase() + value.slice(1)
        }
    }
})
</pre>

필터는 체이닝이 가능하다.
<pre>
{{ message | filterA | filterB }}
</pre>

필터는 Javascript 함수이므로 전달인자를 사용할 수 있다.
<pre>
{{ message | filterA('arg1', arg2) }}
</pre>

## 약어
가장 자주 사용되는 v-bind, v-on 에 대해 특별한 약어를 제공한다.

### v-bind 약어
<pre>
&lt;a v-bind:href="url"&gt;&lt;/a&gt;
&lt;a :href="url"&gt;&lt;/a&gt;
</pre>

### v-on 약어
<pre>
&lt;a v-on:click="doSomething"&gt;&lt;/a&gt;
&lt;a @click="doSomething">&lt;/a&gt;
</pre>
