<template>
  <div>
    <h1>이미지 파일</h1>
    <p>
      파일 타입에는 v-model 디렉티브를 사용할 수 없다.<br />리엑티브 데이터와
      동기화할 때는 v-bind:src를 사용한다.
    </p>
    <div>
      <img :src="imgSrc1" :alt="imgAlt1" />
    </div>

    <hr />
    <p>
      이미지의 src에 data에서 선언한 변수를 연결한 뒤<br />이미지를 클릭하면
      if문 분기를 이용해서 이미지가 변경되는 코드
    </p>
    <p>
      img :src="require(`@/asset/images/${변수명}.png`)" <br />
      img :src='`URL 주소 입력${변수명}`'
    </p>

    <!-- https://www.flaticon.com/packs/brunch-19 -->
    <div>
      <img
        :src="require(`@/assets/images/${imgSrc2}.png`)"
        :alt="imgAlt2"
        @click="changeImg2"
      />
    </div>

    <hr />
    <hr />
    <h1>여러 개의 속성 데이터 바인딩하기</h1>
    <p>
      대량의 속성을 각각의 속성에 바인딩하면 가독성이 크게 떨어지고<br />
      이후에 수정하는 것도 어렵다.<br />
      한 번에 바인딩하면 관리도 쉽고 템플릿의 가독성도 굉장이 향상된다.
    </p>
    <p>매개변수로 전달된 v-bind와 함께 특정 요소만을 따로 지정할 수 있다.</p>
    <div>
      <img v-bind="item" :id="'thumb-' + item.id" />
    </div>
    <hr />
    <hr />
    <h1>require()와 import()</h1>
    <p>
      require나 import 키워드를 통해 외부 라이브러리를 불러온다.<br />두 개의
      키워드 모두 하나의 파일에서 다른 파일의 코드를 불러온다는 동일한 목적을
      가지고 있다.
    </p>
    <p>
      require는 NodeJS에서 사용되고 있는 CommonJS 키워드<br />
      import는 ES6(ES2015)에서 새롭게 도입된 키워드
    </p>
    <dl>
      <dt>const moment = require("moment");</dt>
      <dd>
        CommonJS 방식은 require 키워드를 사용하여 변수를 할당하듯이 모듈을
        불러온다.
      </dd>
      <dt>import moment from "moment";</dt>
      <dd>
        ES6 방식은 Java나 Python처럼 import 키워드를 사용하여 좀 더 명시적으로
        모듈을 불러온다.
      </dd>
    </dl>

    <hr />
    <hr />
    <h1>SVG 데이터 바인딩하기</h1>
    <p>
      SVG의 DOM도 데이터 바인딩할 수 있다.<br />
      간단하게 멋진 UI 조작과 움직이는 그래프 등을 구현할 수 있다.
    </p>
    <div class="box">
      <svg xmlns="http://www.w3.org/2000/svg" version="1.1">
        <circle cx="50%" cy="50%" v-bind:r="radius" fill="lightpink" />
      </svg>
      <input type="range" min="0" max="100" v-model="radius" />
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      imgSrc1: require("@/assets/images/4825330.png"),
      imgAlt1: "허브차",
      imgSrc2: "soup",
      imgAlt2: "수프",

      item: {
        src: require("@/assets/images/4825553.png"),
        alt: "아이콘",
        width: 200,
        height: 200,
        title: "피자",
        id: 1,
      },

      radius: 10,
    };
  },
  methods: {
    changeImg2() {
      if (this.imgSrc2 === "soup") {
        this.imgSrc2 = "breakfast";
        this.imgAlt2 = "초밥";
      } else {
        this.imgSrc2 = "soup";
        this.imgAlt2 = "수프";
      }
    },
  },
};
</script>

<style scoped>
.box {
  display: flex;
  justify-content: center;
  align-items: center;
}
.box svg {
  border: 1px solid;
  min-height: 300px;
  text-align: center;
}
</style>
