# 계산된 속성과 감시자 (Computed Properties and Watchers)

## 계산된 속성 (Computed Properties)
템플릿 내에서 사용하는 표현식은 매우 편리하지만 단순한 연산에만 사용해야 한다.
복잡한 로직의 경우 반드시 <strong>계산된 속성</strong>을 사용해야 한다.
<pre>
&lt;div id="example"&gt;
    &lt;p&gt;원본 메시지: "{{ message }}"&lt;/p&gt;
    &lt;p&gt;뒤집히도록 계산된 메시지: "{{ reversedMessage }}"&lt;/p&gt;
&lt;/div&gt;

var vm = new Vue({
    el: '#example',
    data: {
        message: '안녕하세요'
        },
        computed: {
        // 계산된 getter
        reversedMessage: function () {
            // `this` 는 vm 인스턴스를 가리킵니다.
            return this.message.split('').reverse().join('')
        }
    }
})
</pre>
