<template>
  <div>
    <h1>V-model</h1>
    <p>
      입력 양식의 값 또는 선택 값을 데이터와 동기화하는 양방향 데이터 바인딩<br />
      input에 입력한 값이 바로 출력됨
    </p>
    <p>
      v-model 디렉티브는 다음 두 가지 처리를 한 번에 할 수 있게 해 준다.<br />
      1. 데이터 바인딩으로 요소의 value 속성 변경하기<br />
      2. 이벤트 핸들링으로 받은 값을 데이터에 대입하기
    </p>
    <p>
      v-model을 사용하면 속성으로 설정한 값은 사용하지 않는다.<br />
      따라서 value, checked, selected를 설정해도 이러한 속성은 모두 무시된다.
    </p>

    <hr />
    <hr />

    <h2>input 입력</h2>
    <dl>
      <dt>숫자, 영문은 v-model을 사용하여 양방향이 가능</dt>
      <hr />
      <dd><input type="text" v-model="message1" /> : {{ message1 }}</dd>

      <dt>
        그러나 윈도우 환경에서<br />
        한국어, 일본어, 중국어 처럼 IME 입력 확정 처리가 필요한 경우<br />
        입력이 확정되기 전까지 데이터를 변경하지 않는다.<br />
        만약 확정 전에 데이터를 변경하고자 한다면<br />
        input이벤트를 활용한다.<br />
        이렇게 되면 단방향이 된다.
      </dt>
      <hr />
      <dd>
        v-model로 한글 바인딩 : <input type="text" v-model="message2" />
        {{ message2 }}
      </dd>
      <dd>
        input이벤트로 한글 바인딩 :
        <!-- <input
          type="text"
          @input="(e) => (this.message3 = e.target.value)"
          value="안녕하세요"
          /> -->
        <input type="text" v-on:input="inputMessage3" v-bind:value="message3" />
        {{ message3 }}
      </dd>

      <dt>v-model로 받은 데이터의 자료형</dt>
      <hr />
      <dd>
        input 폼을 사용하여 입력값을 받는 경우 무엇을 입력해도 문자 자료형이
        된다.
      </dd>
      <!-- 무조건 모든 입력값을 문자 자료형으로 인식 -->
      <dd><input type="text" v-model="num1" /> : {{ typeof num1 }}</dd>
      <hr />
      <dd>
        자동으로 숫자 자료형으로 바꾸어 주는 방법으로 v-model.number 사용할 수
        있다.
      </dd>
      <!-- 123abc 입력하면 뒤의 문자열은 무시되고 123만 남음, abc123 입력하면 문자 자료형 -->
      <dd><input type="text" v-model.number="num2" /> : {{ typeof num2 }}</dd>
      <hr />
      <dd>input폼의 타입을 number로 지정하면 좀 더 명확하다.</dd>
      <!-- 무조건 숫자 자료형만 입력 -->
      <dd><input type="number" v-model.number="num3" /> : {{ typeof num3 }}</dd>
    </dl>

    <hr />
    <hr />
    <h2>textarea 입력</h2>
    <dl>
      <dt>데이터를 문자열로 다룬다.</dt>
      <dd>
        <textarea
          name=""
          id=""
          cols="30"
          rows="10"
          v-model="multiMessage1"
        ></textarea>
      </dd>
      <dd>{{ multiMessage1 }}</dd>

      <hr />

      <dd>
        <textarea
          name=""
          id=""
          cols="30"
          rows="10"
          @input="inputMutiMessage2"
          v-bind:value="multiMessage2"
        ></textarea>
      </dd>
      <dd>{{ multiMessage2 }}</dd>
    </dl>
  </div>
</template>

<script>
export default {
  data() {
    return {
      message1: "Hell, Vue.js",
      message2: "안녕하세요",
      message3: "좋은 날이네요",
      num1: 1,
      num2: 1,
      num3: 1,
      multiMessage1: "v-model로 입력해요",
      multiMessage2: "input 이벤트로 입력해요",
    };
  },
  methods: {
    inputMessage3(e) {
      this.message3 = e.target.value;
    },
    inputMutiMessage2(e) {
      this.multiMessage2 = e.target.value;
    },
  },
};
</script>

<style scoped></style>
