<template>
  <div>
    <h1>선택박스</h1>
    <dl>
      <dt>하나의 요소 선택</dt>
      <hr />
      <dd>데이터를 문자열로 다룬다.</dd>
      <dd>
        select에 v-model을 부여하고, 값을 선택하면 option value에 해당하는 값이
        v-model의 값에 입력된다.
      </dd>
      <dd>
        <select v-model="selectData1">
          <option disabled="disabled">선택하세요</option>
          <option value="최성윤">성윤</option>
          <option value="김지범">지범</option>
          <option value="봉재현">재현</option>
          <option value="홍주찬">주찬</option>
          <option value="손영택">영택</option>
          <option value="이장준">장준</option>
        </select>
      </dd>
      <dd>{{ selectData1 }}</dd>
      <dd>
        초기값으로 option value에 해당하는 값을 부여하면 해당 option이 선택된
        채로 보인다.
      </dd>
      <dd>
        <select v-model="selectData2">
          <option value="최성윤">성윤</option>
          <option value="김지범">지범</option>
          <option value="봉재현">재현</option>
          <option value="홍주찬">주찬</option>
          <option value="손영택">영택</option>
          <option value="이장준">장준</option>
        </select>
      </dd>
      <dd>{{ selectData2 }}</dd>
      <hr />
      <hr />
      <dt>여러 개의 요소 선택</dt>
      <hr />
      <dd>데이터를 배열로 다룬다.</dd>
      <dd>
        <select v-model="multiSelectData" multiple size="7">
          <option disabled="disabled">다중 선택하세요</option>
          <option value="최성윤">성윤</option>
          <option value="김지범">지범</option>
          <option value="봉재현">재현</option>
          <option value="홍주찬">주찬</option>
          <option value="손영택">영택</option>
          <option value="이장준">장준</option>
        </select>
      </dd>
      <dd>{{ multiSelectData }}</dd>
    </dl>
  </div>
</template>

<script>
export default {
  data() {
    return {
      selectData1: "",
      selectData2: "김지범",
      multiSelectData: [],
    };
  },
};
</script>

<style scoped></style>
