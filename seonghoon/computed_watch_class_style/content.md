# 클래스와 스타일 바인딩

## 클래스 바인딩

### 객체 문법

v-bind:class 디렉티브를 이용하여 데이터 바인딩을 통해 클래스를 조작하고 적용할 수 있습니다.
v-bind:class로 전달되는 클래스 데이터를 담고있는 객체는 객체의 값이 '클래스 이름':Boolean 형태로 이루어져있습니다.
값이 'TRUE'인 클래스 이름들이 적용되고 반대로 값이 'FALSE'인 경우 그 값을 갖고있는 클래스들은 적용되지 않습니다.
또한 class 디렉티브는 일반 클래스 속성과 함께 있을 수 있습니다.

객체 바인딩을 통해 클래스를 선택하는 예
```
<div :class="myClass">
</div>

new Vue({
    ...
    data: {
        myClass: {
            'classA':true,
            'classB':false,
            'classC':true
        }
    }
})
```

위 예제의 경우 classA와 classC가 적용될 것입니다.

..아직 작업중...