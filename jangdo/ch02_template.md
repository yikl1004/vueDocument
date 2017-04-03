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
