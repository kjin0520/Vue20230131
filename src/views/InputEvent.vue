<template>
  <div>
    <h1>입력 양식의 입력 값 추출하기</h1>
    <p>입력 양식의 입력값은 v-model을 사용하면 간단함</p>
    <p>
      그렇긴 하지만 v-on 디렉티브를 사용해서 입력 내용을 확인하고, 데이터에
      할당할 수도 있다.
    </p>
    <p>
      <input type="text" :value="message1" @input="handleInput" />
      {{ message1 }}
    </p>

    <hr />

    <p>
      <input
        type="text"
        :value="message2"
        @input="
          (e) => {
            this.message2 = e.target.value;
          }
        "
      />
      {{ message2 }}
    </p>

    <hr />
    <p>
      <input type="text" v-model="message3" />
      {{ message3 }}
    </p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      message1: "Hello",
      message2: "Hello",
      message3: "Hello",
    };
  },
  methods: {
    handleInput(e) {
      this.message1 = e.target.value;
    },
  },
};
</script>

<style></style>
