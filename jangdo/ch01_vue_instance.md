# Vue 인스턴스
## 생성자
모든 Vue vm(ViewModel)은 Vue 생성자 함수로 root Vue 인스턴스를 생성하여 부트스크래핑된다.
<pre>
var vm = new Vue({
    //옵션
})
</pre>
Vue 인스턴스를 인스턴스화 할 때는 데이터, 템플릿, 마운트할 엘리멘트, 메소드, 라이프사이클 콜백 등의 옵션을 포함 할 수있는 options 객체를 전달 해야한다.

Vue 생성자는 미리 정의 된 옵션으로 재사용 가능한 컴포넌트 생성자를 생성하도록 확장 될 수 있다.
<pre>
var MyComponent = Vue.extend({
  // 옵션 확장
})
// `MyComponent`의 모든 인스턴스는
// 미리 정의된 확장 옵션과 함께 생성됩니다.
var myComponentInstance = new MyComponent()
</pre>

## 속성과 메소드

각 Vue 인스턴스는 data 객체에 있는 모든 속성을 프록시 처리 한다.

<pre>
var data = { a: 1 }
var vm = new Vue({
  data: data
})
vm.a === data.a // -> true

vm.a = 2
data.a // -> 2

data.a = 3
vm.a // -> 3
</pre>
프록시 속성은 반응형이다.
인스턴스를 작성한 후 인스턴스에 새 특성을 첨부하면 뷰 업데이트가 트리거되지 않는다.

### $접두사

Vue 인스턴스는 데이터 속성 외에도 유용한 인스턴스 속성 및 메소드를 제공한다.
이 프로퍼티들과 메소드들은 $ 접두사로 프록시 데이터 속성과 구별된다.

<pre>
var data = { a: 1 }
var vm = new Vue({
  el: '#example',
  data: data
})
vm.$data === data // -> true
vm.$el === document.getElementById('example') // -> true
// $watch 는 인스턴스 메소드 입니다.
vm.$watch('a', function (newVal, oldVal) {
  // `vm.a`가 변경되면 호출 됩니다.
})
</pre>

## 인스턴스 라이프사이클 훅(Hook)

각 Vue 인스턴스는 데이터 관찰을 설정하고, 템플릿을 컴파일하고, 인스턴스를 DOM에 마운트하고, 데이터가 변경 될 때 DOM을 업데이트 해야 할 때 일련의 초기화 단계를 거친다. 이 과정에서 사용자 정의 로직을 실행 할 수있는 <strong>라이프사이클 훅</strong> 도 호출된다.
<pre>
var vm = new Vue({
  data: {
    a: 1
  },
  created: function () {
    // `this` 는 vm 인스턴스를 가리킵니다.
    console.log('a is: ' + this.a)
  }
})
// -> "a is: 1"
</pre>
