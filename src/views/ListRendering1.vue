<template>
  <div>
    <h1>리스트 데이터 출력/변경하기</h1>
    <p>
      모든 프로그래밍 언어에서 반복문을 사용하는 것처럼 vue에도 반복적인
      데이터를 렌더링할 수 있다.
    </p>
    <p>
      리스트 데이터는 배열 혹은 객체를 사용하며 일반적으로는 객체를 사용한다.<br />
      배열은 인덱스, 객체는 id와 같은 유닉크한 키가 있어야 가상 DOM으로 렌더링할
      때 최적화가 이루어진다.
    </p>

    <h2>요소를 반복해서 렌더링하기</h2>
    <p>반복해서 렌더링하고 싶은 태그에 v-for 속성 사용</p>
    <p>
      v-for="각 요소를 할당할 변수명 in 반복대상이 되는 배열 또는 객체"
      v-bind:key="요소 내부의 유니크한 인덱스나 id 속성(권장)"
    </p>
    <p>
      각 요소를 할당할 변수명은 자유이며<br />
      변수 부분을 괄호로 감싸면 배열의 인덱스도 받을 수 있지만 반드시 순서는
      지켜야 한다.<br />
      배열은 값, 인덱스<br />
      객체는 값, 키, 인덱스
    </p>
    <ul>
      <li v-for="item in fruits" :key="item">{{ item }}</li>
    </ul>
    <hr />
    <ul>
      <li v-for="(item, index) in fruits" :key="item">
        {{ index }} : {{ item }}
      </li>
    </ul>
    <hr />
    <hr />
    <ul>
      <li v-for="(item, key, index) in list1" :key="key">
        {{ index }} : {{ key }} :{{ item }}
      </li>
    </ul>
    <hr />
    <hr />
    <ul>
      <li v-for="item in list2" :key="item.id">
        {{ item.id }} : {{ item.name }} : {{ item.order }}
      </li>
    </ul>
    <hr />
    <ul>
      <li v-for="(item, index) in list2" :key="item.id">
        {{ index }} : {{ item.id }} : {{ item.name }} : {{ item.order }}
      </li>
    </ul>
    <hr />
    <ul>
      <li v-for="(item, key, index) in list2" :key="item.id">
        {{ index }} : {{ item.id }} : {{ item.name }} : {{ item.order }}
      </li>
    </ul>

    <hr />
    <hr />
    <h2>키의 역할</h2>
    <p>
      리스트를 변경할 때 요소의 식별과 효울적인 렌더링 처리를 위해 요소에
      유니크한 key 속성을 설정해야 한다.<br />
      :key="1"로 문자열을 지정할 수 있지만 반복으로 모두 같은 '1'이 지정되어
      버리면 아무 의미가 없다. <br />
      따라서 요소 내부의 유니크 ID인 id 속성을 키로 데이터 바인딩 해야 한다.
    </p>
    <p>
      요소의 제거와 정렬 등을 고려하려면 변하지 않는 유니크 키를 사용해야
      한다.<br />
      예를 들어 배열의 인덱스는 유니크하지만 요소를 제거하거나 섞으면 변하게
      된다.
    </p>
    <p>
      같은 부모 요소 내에 있을 경우 다른 v-for라고 해도 키가 중복되면 안된다.<br />
      [Vue warn]이 뜬다.
    </p>
    <!-- <ul>
      <li v-for="item in fruits" :key="item">{{ item }}</li>
      <li v-for="item in fruits" :key="item">{{ item }}</li>
    </ul> -->
  </div>
</template>

<script>
export default {
  data() {
    return {
      fruits: ["사과", "복숭아", "수박", "포도"],
      list1: {
        apple: "사과",
        peach: "복숭아",
        watermelon: "수박",
        grape: "포도",
      },
      list2: [
        { id: 950731, name: "최성윤", order: 2 },
        { id: 970303, name: "이장준", order: 3 },
        { id: 990104, name: "봉재현", order: 6 },
        { id: 990203, name: "김지범", order: 7 },
      ],
    };
  },
};
</script>

<style></style>
