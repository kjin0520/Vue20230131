<template>
  <div>
    <h1>텍스트 바인딩</h1>
    <dl>
      <dt>Mustache 기법</dt>
      <dt>텍스트 콘텐츠를 위한 기법</dt>
      <hr />
      <dd>해당 위치에 data에서 정의한 속성의 속성값 바인딩</dd>
      <dd>Hello {{ message1 }}</dd>
      <dd>{{ message2.value3 }}</dd>
      <dd>{{ message2.value3.length }}</dd>
      <dd>{{ list }}</dd>
      <dd>{{ list.length }}</dd>
      <dd>{{ list[2] }}</dd>
      <dd>{{ list[num] }}</dd>
      <hr />
      <hr />

      <dt>Mustache 안에서 표현식 작성 가능</dt>
      <dt>단, 표현식이 아닌 문장 작성은 안됨</dt>
      <hr />
      <dt>표현식 : 값을 만들어 내는 코드</dt>
      <!-- <dd>{{ var fruits = num }}</dd> -->
      <dd>{{ message2.value > 10 ? "10자 이상" : "10자 미만" }}</dd>
      <dd>{{ Math.round(3.14) }}</dd>
      <hr />
      <hr />
    </dl>

    <h1>템플릿 제어 디렉티브</h1>
    <dl>
      <dt>v-html : HTML 태그를 그대로 렌더링하기</dt>
      <hr />
      <dd v-html="message3"></dd>
      <dd>
        다만 v-html을 권장하지 않는다.<br />
        스크립트 삽입이 가능하기 떄문에 XSS 공격에 취약해질 수 있다.
      </dd>
      <hr />
      <hr />

      <dt>v-text : Mustache 대신 텍스트 콘텐츠로 렌더링하기</dt>
      <hr />
      <dd>
        요소 내부의 텍스트 콘텐츠가 단일 Mustache 만으로 구성되어 있을 경우
        Mustache 대신 사용할 수 있다.
      </dd>
      <dd v-text="message3"></dd>
      <hr />
      <hr />

      <dt>v-pre : 템플릿 컴파일 생략하기</dt>
      <hr />
      <dd v-pre>{{ message3 }}</dd>
      <hr />
      <hr />

      <dt>
        v-once : 템플릿을 한 번만 컴파일하고 이후에는 정적 콘텐츠로 다루고 싶을
        때 사용
      </dt>
      <hr />
      <dd v-once>{{ message4 }}</dd>
      <hr />
      <hr />

      <dt>v-cloak : 인스턴스 준비가 끝나면 자동으로 제거된다.</dt>
      <hr />
      <dd>
        인스턴스가 생성될 때까지 Mustache 등의 컴파일 이전 단계의 템플릿이
        화면에 출력되는 것을 막을 수 있다.
      </dd>
      <dd class="cloak-in" v-cloak>
        {{ message3 }}
      </dd>
      <hr />
      <hr />
    </dl>
  </div>
</template>

<script>
export default {
  data() {
    return {
      message1: "2023년 2월 1일",
      message2: {
        value1: "React",
        value2: "Angular",
        value3: "Vue.js",
      },
      list: ["바나나", "사과", "귤"],
      num: 0,
      message3:
        "<span onclick='console.log(`test`)'>Hello <strong>Vue.js</strong></span>",
      message4: "v-once",
    };
  },
  created() {
    setTimeout(() => {
      this.message4 = "3초 후 한 번만 바인딩";
    }, 3000);
  },
};
</script>

<style scoped>
h1 {
  border-top: 2px solid #eee;
  border-bottom: 2px solid #eee;
  padding-top: 20px;
  padding-bottom: 20px;
}
dl {
  margin: 50px 30px 100px;
}
dt {
  font-weight: bold;
}
/* v-cloak */
[v-cloak] {
  display: none;
}
@keyframes cloakIn {
  0% {
    opacity: 0;
  }
}
.cloak-in {
  animation: cloakIn 1s;
}
.cloak-in[v-cloak] {
  opacity: 0;
}
</style>
