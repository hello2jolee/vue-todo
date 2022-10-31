# 할 일 관리 앱

## 이벤트 발생과 수신 형식
- 이벤트 발생과 수신은 `$emit()`과 `v-on:` 속성을 사용하여 구현
    ```javascript
    // $emit('이벤트 이름', 인자1, 인자2, ...) 

    this.$emit('이벤트명')
    ```
    ```html
    <child-component v-on:이벤트명="상위 컴포넌트의 메서드명"></child-component>
    ```


## `V-`로 시작하는 디렉티브
#### `v-model` 이란?
- v-model 디렉티브의 값에 사용자 입력과 동기화할 데이터를 지정
- 인풋 박스에 텍스트를 입력했을 때 뷰 인스턴스에서 텍스트 값을 인식할 수 있게 v-model을 사용
    ```html
    <div id="app">
        <input v-model="message">
        <p>{{ message }}</p>
    </div>
    ```
    ```javascript
    new Vue({
        el: '#app',
        data: {
            message: 'HELLO'
        }
    })
    ```

#### `v-on:click` 이란?
- 버튼을 클릭했을 때 특정 동작을 수행할 수 있게 v-on:click을 사용
    ```html
    <!-- 두 템플릿은 완전히 같은 의미를 가지고 있음 -->

    <button v-on:click="handleClick">클릭</button>
    <button @click="handleClick">클릭</button>
    ```

    ```javascript
    new Vue({
        el: '#app',
        methods: {
            handleClick: function() {
                alert('클릭했어요')
            }
        }
    })
    ```
- `v-on:keyup.enter`을 사용하면 엔터키를 눌렀을 때 동작하도록 할 수 있음

#### `v-for` 이란?
- 기사 목록 또는 상품 목록과 같은 리스트는 data 옵션에 등록한 배열 또는 객체에 v-for 디렉티브를 적용해서 반복 렌더링할 수 있음
- v-for 디렉티브로 반복한 요소는 모두 뷰에서 내부적으로 인텍스를 부여
- 뷰 데이터의 아이템 개수만큼 화면에 가져올 때 사용
    ```html
    <template>
        <section>
            <ul>
                <li v-for="todoItem in todoItems">{{ todoItem }}</li>
            </ul>
        </section>
    </template>
    ```

#### `v-bind` 란?
- 아이디, 클래스, 스타일 등의 HTML 속성(attributes) 값에 뷰 데이터 값을 연결할 때 사용하는 데이터 연결 방식
    ```html
    <div id="app">
        <p v-bind:id="idA">아이디 바인딩</p>
    </div>
    ```
    ```javascript
    new Vue({
        el: '#app',
        data: {
            idA: 10
        }
    })
    ```

## STYLE 관련 속성
#### `<style scoped>` 란?
- 스타일 정의를 해당 컴포넌트에만 적용할 때 사용
