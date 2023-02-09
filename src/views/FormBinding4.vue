<template>
  <div>
    <h1>v-bind</h1>
    <p>
      v-bind 디렉티브를 이용하여 동적으로 각종 태그들의 속성값을 바인딩해 줄 수
      있다
    </p>
    <dl>
      <dt>select 속성에 데이터 바인딩</dt>
      <hr />
      <dd>
        <select name="" id="" v-model="selectDataBinding">
          <option :value="mem2">{{ mem2 }}</option>
          <option :value="mem3">{{ mem3 }}</option>
          <option :value="mem6">{{ mem6 }}</option>
          <option :value="mem7">{{ mem7 }}</option>
          <option :value="mem9">{{ mem9 }}</option>
        </select>
      </dd>
      <dd>{{ selectDataBinding }}</dd>
      <hr />
      <hr />

      <dt>checkbox 속성에 데이터 바인딩</dt>
      <hr />
      <dd>
        <input type="checkbox" :value="apple" v-model="chkDataBinding" />{{
          apple
        }}
        <input type="checkbox" :value="orange" v-model="chkDataBinding" />{{
          orange
        }}
        <input type="checkbox" :value="banana" v-model="chkDataBinding" />{{
          banana
        }}
        <input type="checkbox" :value="grape" v-model="chkDataBinding" />{{
          grape
        }}
      </dd>
      <dd>{{ chkDataBinding }}</dd>
      <hr />
      <hr />

      <dt>radio 속성에 데이터 바인딩</dt>
      <hr />
      <dd>
        <input type="radio" :value="female" v-model="radioDataBinding" />{{
          female
        }}
        <input type="radio" :value="male" v-model="radioDataBinding" />{{
          male
        }}
      </dd>
      <dd>{{ radioDataBinding }}</dd>
    </dl>
  </div>
</template>

<script>
export default {
  data() {
    return {
      selectDataBinding: "김지범",
      mem2: "최성윤",
      mem3: "이장준",
      mem6: "봉재현",
      mem7: "김지범",
      mem9: "홍주찬",

      chkDataBinding: [`오렌지`, `바나나`],
      apple: "사과",
      orange: "오렌지",
      banana: "바나나",
      grape: "포도",

      radioDataBinding: "여성",
      female: "여성",
      male: "남성",
    };
  },
};
</script>

<style></style>
