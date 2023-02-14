<template>
  <div>
    <h1>반복 렌더링하면서 다양한 조건 적용하기</h1>
    <h2>조건을 사용해서 클래스 조작하기</h2>
    <ul>
      <li
        v-for="member in list1"
        :key="member.id"
        :class="{ love: member.order > 4 }"
      >
        {{ member.name }}은
        <span v-if="member.order > 4">나의 최애입니다. </span>
        <span v-else>나의 최애가 아닙니다. </span>
      </li>
    </ul>
    <hr />

    <!-- v-for와 v-if는 함께 사용할 수 없다. -->
    <!-- 
    <ul>
      <li v-for="member in list1" :key="member.id" v-if="member.order > 4">
        {{ member.name }} - {{ member.order }}
      </li>
    </ul> -->

    <!-- 배열에 조건적인 부분을 출력할 때 -->
    <!-- 배열 메소드(map, filter, reduce, some, sort 등) 사용-->
    <ul>
      <li v-for="member in list1.filter((m) => m.order > 4)" :key="member.id">
        {{ member.name }} - {{ member.order }}
      </li>
    </ul>

    <hr />
    <hr />

    <h2>리스트 변경하기</h2>
    <p>
      리스트 요소 변경도 일반적인 자바스크립트에서 배열 또는 객체를 변경할 때와
      크게 다르지 않다.
    </p>
    <p>다만, 다음 두 가지 경우에는 변경을 감지할 수 없으므로 주의</p>
    <ul>
      <li>인덱스 숫자를 사용한 배열 요소 변경</li>
      <li>이후에 추가된 속성 변경</li>
    </ul>

    <h3>리스트에 요소 추가하기</h3>
    <p>
      배열의 push나 unshift 사용<br />
      this.list.push(새로운값)
    </p>

    <h3>리스트에서 요소 제거하기</h3>
    <p>특정 요소를 리스트에서 제거할 때는 배열 메서드인 splice() 사용</p>

    <h3>리스트 요소 속성 변경하기</h3>
    <p>제거하기와 마찬가지로 배열의 인덱스를 매개변수로 전달</p>

    <div>
      <p>동물이름 : <input type="text" v-model="name" /></p>
      <p>
        <button @click="doAdd">동물 추가하기</button>
      </p>
      <ul>
        <li v-for="(animal, index) in list2" :key="animal.id">
          <span v-if="animal.hp < 100">무서운 동물 --- </span>
          {{ animal.name }} - {{ animal.hp }}

          <!-- 삭제 버튼 v-for 내부에 만들기 -->
          <button @click="doRemove(index)">제거하기</button>
          <button @click="doAttack(index)">공격하기</button>
        </li>
      </ul>

      <hr />
      <hr />
      <h2>외부에서 데이터 가져와서 출력하기</h2>
      <p>
        데이터가 외부에 있는 경우 일단, JSON 파일 또는 웹 API를 사용해서
        가져온다.
      </p>
      <p>Ajax 라이브러리 axios 사용</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      list1: [
        { id: 950731, name: "최성윤", order: 2 },
        { id: 970303, name: "이장준", order: 3 },
        { id: 990104, name: "봉재현", order: 6 },
        { id: 990203, name: "김지범", order: 7 },
      ],
      name: "",
      list2: [
        { id: 1, name: "기린", hp: 100 },
        { id: 2, name: "사자", hp: 200 },
        { id: 3, name: "호랑이", hp: 500 },
      ],
    };
  },
  methods: {
    doAdd: function () {
      // 리스트 내부에서 가장 큰 ID 추출하기
      // reduce() : 배열의 각 요소에 대해 주어진 리듀서 (reducer) 함수를 실행하고, 하나의 결과값을 반환
      // arr.reduce(callback[, initialValue])
      const max = this.list2.reduce(function (a, b) {
        return a > b.id ? a : b.id;
      }, 0);
      const hpNum = Math.floor(Math.random() * 500);

      // 새로운 동물을 리스트에 추가하기
      this.list2.push({
        id: max + 1,
        name: this.name,
        hp: hpNum + 100,
      });
    },
    doRemove: function (i) {
      this.list2.splice(i, 1);
    },
    doAttack: function (i) {
      this.list2[i].hp -= 2;
    },
  },
};
</script>

<style scoped>
.love {
  font-weight: bold;
  color: yellowgreen;
}
</style>
