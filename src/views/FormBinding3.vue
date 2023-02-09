<template>
  <div>
    <h1>체크박스</h1>
    <dl>
      <dt>하나의 요소를 선택</dt>
      <hr />
      <dd>하나의 요소를 선택하는 체크박스는 데이터를 boolean으로 다룬다.</dd>
      <dd>데이터의 값이 true면 선택된 상태</dd>
      <dd><input type="checkbox" v-model="chk1" /> {{ chk1 }}</dd>
      <dd>
        true-value와 false-value라는 특별한 속성을 사용하여 true와 false의 값
        자체를 지정할 수도 있다.
      </dd>
      <dd>
        <input
          type="checkbox"
          v-model="chk2"
          true-value="yes"
          false-value="no"
        />
        {{ chk2 }}
      </dd>
      <hr />
      <hr />
      <dt>여러 개의 요소를 선택</dt>
      <hr />
      <dd>여러 개의 요소를 선택하는 체크박스는 데이터를 배열로 다룬다.</dd>
      <dd>
        v-model에 모두 같은 배열 데이터를 지정하고 각 요소에 value 속성을
        설정하는 형태로 사용한다.
      </dd>
      <dd>
        <input type="checkbox" value="최성윤" v-model="multiChk" />성윤
        <input type="checkbox" value="김지범" v-model="multiChk" />지범
        <input type="checkbox" value="홍주찬" v-model="multiChk" />주찬
        <input type="checkbox" value="이장준" v-model="multiChk" />장준
        <input type="checkbox" value="봉재현" v-model="multiChk" />재현
      </dd>
      <dd>{{ multiChk }}</dd>
    </dl>
    <h1>라디오 버튼</h1>
    <dl>
      <dt>데이터를 문자열로 다룬다.</dt>
      <hr />
      <dd>
        <input type="radio" value="여성" v-model="radioData" />여성
        <input type="radio" value="남성" v-model="radioData" />남성
      </dd>
      <dd>{{ radioData }}</dd>
    </dl>
  </div>
</template>

<script>
export default {
  data() {
    return {
      chk1: true,
      chk2: null,
      multiChk: [],
      radioData: "여성",
    };
  },
};
</script>

<style scoped></style>
