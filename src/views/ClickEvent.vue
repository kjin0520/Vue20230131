<template>
  <div>
    <h1>이벤트 핸들링</h1>
    <dl>
      <dt>이벤트핸들러</dt>
      <dd>'버튼을 클릭했을 때'라는 DOM 이벤트를 받아서 처리하는 것</dd>
      <dd>즉, 이벤트의 처리 내용</dd>

      <dt>핸들</dt>
      <dd>이벤트 핸들러를 이벤트와 연결하는 것</dd>
      <dd>
        자바스크립트는 addEventListener 메서드, jQuery는 $(element).on 메서드
      </dd>
      <dd>Vue.js는 템플릿 내부에 v-on 디렉티브</dd>
    </dl>

    <h2>메서드 이벤트 핸들러</h2>
    <p>컴포넌트의 methods 옵션에 정의되어 있는 메서드 이름 지정</p>
    <p>v-on은 생략하고 '@'라고 작성할 수 있다.</p>
    <p>{{ message }}</p>
    <button @click="handleClick">click me</button>

    <hr />

    <p>{{ count1 }}</p>
    <p>
      <button @click="increase">증가</button>
      <button @click="decrease">감소</button>
    </p>

    <h2>인라인 메서드 핸들링</h2>
    <p>
      인라인 메서드 핸들링이란, 디렉티브의 값에 자바스크립트 식을 직접 작성하는
      것
    </p>
    <p>
      인라인 메서드 핸들러의 식에서는 이벤트 객체 또는 사용자 정의 이벤트
      매개변수를 $event라는 변수 이름으로 사용할 수 있다.
    </p>
    <p>{{ count2 }}</p>
    <button @click="count2++">click me</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      message: "아직 클릭전입니다.",
      count1: 0,
      count2: 0,
    };
  },
  methods: {
    handleClick() {
      console.log("클릭했어요.");
      this.message = "클릭했어요.";
    },
    increase() {
      this.count1++;
    },
    decrease() {
      this.count1--;
    },
  },
};
</script>

<style></style>
