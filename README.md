# learn-vue-js
<br>

> [follow Captain's teaching 🦸‍♂️](https://joshua1988.github.io/vue-camp/vue/instance.html#%EC%9D%B8%EC%8A%A4%ED%84%B4%EC%8A%A4-%EC%83%9D%EC%84%B1)
[the other](https://dahye-jeong.gitbook.io/vue-js/)

<br>
<br>

## Vue 란?
MVVM 패턴의 뷰모델(ViewModel) 레이어에 해당하는 화면(View)단 라이브러리

<image src="https://012.vuejs.org/images/mvvm.png">
- View : DOM 형태의 html 코드 구성
- View Model 
    - DOM Listener : DOM의 이벤트를 감지하고 JS Model에게 로직을 요구
    - Data Bindings : 로직 처리를 화면에 반환
- Model : `Plain JavaScript Objects`. 데이터 로직 처리

<br>

---

<br>

### 뷰 인스턴스
뷰로 개발할 때 필수로 생성해야하는 **기본 단위**

```javascript
new Vue({
  el: ,         // 대상이 되는 요소{html element, css selector}
  template: ,   // 화면에 표시할 마크업 요소 정의
  data: ,       // 뷰의 반응성이 반영된 속성
  methods: ,    // vue 인스턴스에 사용되는 화면 로직제어 관련 메소드 정의
  created: ,    // 뷰 라이프사이클 속성
  watch: ,      // data 속성 값이 변화했을 때 추가 동작 수행 정의
});
```

<br>

---

<br>

### 뷰 컴포넌트
화면을 구성하는 영역을 구분하고 재사용성을 높임

##### 컴포넌트간 데이터 통신
- `props` : 상위 컴포넌트의 데이터를 하위 컴포넌트에게 전달. 데이터 반응형 O
    ```javascript
    <app-header v-bind:프롭스 속성이름 ="상위 컴포넌트 데이터 이름"></app-header>

    // ...

    let appHeader = {
        template: '<h1>{{ 프롭스 속성이름 }}</h1>',
        // Root에 있는 데이터를 하위 컴포넌트인 app-header에게 props
        props: ['프롭스 속성이름']
    }
    ```
- `events` : 하위 컴포넌트에서 상위 컴포넌트로 이벤트를 올림
    ```javascript
    <app-header v-on:하위컴포넌트 발생 이벤트 이름="상위 컴포넌트 메서드 이름"></app-header>
    
    // ...

    let appHeader = {
        template: '<button v-on:click="passEvent">click</button>',
        methods: {
            passEvent: function(){
                this.$emit('pass');         // 이벤트 발생
            }
        }
    }

    // ...

    new Vue({
    el: '#상위컴포넌트',
    components: {
        'app-header': appHeader
    },
    methods: {
        상위컴포넌트메서드이름: function(){
            console.log('text logging');
        }
    }
    })

    ```