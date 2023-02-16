<template>
  <div>
    <h1>Change</h1>
    <select
      name=""
      id=""
      :value="selectedValue1"
      @change="handleChange($event)"
    >
      <option value="member7">김지범</option>
      <option value="member6">봉재현</option>
      <option value="member4">손영택</option>
      <option value="member3">이장준</option>
    </select>
    <p>{{ selectedValue1 }}</p>

    <hr />
    <select name="" id="" v-model="selectedValue2">
      <option value="member7">김지범</option>
      <option value="member6">봉재현</option>
      <option value="member4">손영택</option>
      <option value="member3">이장준</option>
    </select>
    <p>{{ selectedValue2 }}</p>

    <hr />
    <p>v-model을 사용하면 간단함</p>
    <p>
      $event 파라미터는 해당 태그의 이벤트에 관한 파라미터이며 event를 받고 싶을
      때는 함수명($event)로 입력하면 된다.
    </p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      selectedValue1: "member7",
      selectedValue2: "member3",
    };
  },
  methods: {
    handleChange(e) {
      console.log(e.target.value);
      this.selectedValue1 = e.target.value;
    },
  },
};
</script>

<style></style>
