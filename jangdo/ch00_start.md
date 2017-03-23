# Vue js

## v-
v-bind 속성은 디렉티브 라고 부른다.
<pre>
v- 접두어 : 렌더링 된 DOM에 특수한 반영형 동작을 한다.
</pre>

### v-bind
v-bind 속성은 디렉티브라고 부른다.<br>
디렉티브는 Vue에서 제공하는 특수 속성임을 나타낸다.
<pre>
&lt;div id="app-2"&gt;
    &lt;span v-bind:title="message"&gt;
        마우스 올렸을 시 이벤트 발생
    &lt;/span&gt;
&lt;/div&gt;
var app2 = new Vue({
  el: '#app-2',
  data: {
    message: '이 페이지는 ' + new Date() + ' 에 로드 되었습니다'
  }
})
</pre>

### 조건문과 반복문

#### seen
텍스트와 속성뿐 아니라 DOM의 구조에도 데이터를 바인딩 할 수 있다.
또한 Vue 엘리멘트가 Vue에 삽입/갱신/제거될 때 자동으로 전환 효과를 적용할 수 있다.
<pre>
&lt;div id="app-3"&gt;
    &lt;p v-if="seen"&gt;
        이제 나를 볼 수 있어요.
    &lt;/p&gt;
&lt;/div&gt;
var app3 = new Vue({
  el: '#app-3',
  data: {
    seen: true
  }
})
</pre>

#### for
배열의 데이터를 사용해 항목 목록을 표시하는데 사용한다.

<pre>
&lt;div id="app-4"&gt;
    &lt;ul&gt;
        &lt;li v-for="todo in todos"&gt;
            {{ todo.text }}
        &lt;/li&gt;
    &lt;//ul&gt;
&lt;/div&gt;
var app4 = new Vue({
  el: '#app-4',
  data: {
    todos:[
        {text:'JavaScript 배우기'},
        {text:'Vue 배우기'},
        {text:'무언가 멋진 것을 만들기'}
    ]
  }
})
</pre>
app4.todos.push({text:'New todos'}) 를 입력하여 목록에 새 항목을 추가할 수 있다.

## 사용자 입력 핸들링
사용자가 앱과 상호 작용할 수 있게 하기 위해 v-on 디렉티브를 사용하여 Vue 인스턴스에 메소드를 호출하는 이벤트 리스너를 첨부 할 수 있다.

### v-on
<pre>
&lt;div id="app-5"&gt;
    &lt;p&gt;{{ message }}&lt;/p&gt;
    &lt;button v-on:click="reverseMessage"&gt;메세지 뒤집기&lt;/button&gt;
&lt;/div&gt;
var app5 = new Vue({
    el: '#app-5',
    data: {
        message: 'Hi'
    },
    methods:{
        reverseMessage : function(){
          this.message = this.message.split('').reverse().join('')
        }
    }
})
</pre>
DOM을 건드리지 않고 앱의 상태를 업데이트 할 수 있다.
모든 DOM조작은 Vue에 의해 처리되며 작성한 코드는 기본 로직에만 초점을 맞춘다.

### v-model
양식에 대한 입력과 앱 상태를 양방향으로 바인딩 시킬 때 사용
<pre>
&lt;div id="app-6"&gt;
    &lt;p&gt;{{ message }}&lt;/p&gt;
    &lt;input v-model="message"&gt;
&lt;/div&gt;
var app6 = new Vue({
    el: '#app-6',
    data: {
        message: 'Hi'
    }
})
</pre>

## 컴포넌트
본질적으로 미리 정의된 옵션을 가진 Vue 인스턴스이다.
<pre>
&lt;ol&gt;
    &lt;todo-item&gt;&lt;/todo-item&gt;
&lt;/ol&gt;

</pre>
