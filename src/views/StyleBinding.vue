<template>
  <div>
    <h1>클래스와 스타일 데이터 바인딩</h1>
    <p>:style, :class에 object 형태로 key:value(클래스명, boolean)값을 부여</p>
    <p>해당 클래스에 대해 동적으로 조절이 가능하다.</p>
    <hr />
    <p
      :style="{ color: textColor, backgroundColor: bgColor }"
      :class="{ bold: isBold, italic: isItalic }"
    >
      골든차일드 봉재현
    </p>
    <p
      :class="{
        bulColor: isColor,
        'bg-color': isBg,
        bold: isBold,
        italic: isItalic,
      }"
    >
      골든차일드 김지범
    </p>

    <p>
      <button @click="isBold = !isBold">글자 굵게</button>
      <button @click="isItalic = !isItalic">글자 기울이기</button>
    </p>
    <hr />

    <h2>플레인 속성과 함께 사용하는 경우</h2>
    <p>
      데이터 바인딩을 하지 않은 플레인 속성과 함께 사용하는 경우<br />렌더링
      결과를 보면 알 수 있듯 바인딩하는 것이 덮어쓰게 된다.
    </p>
    <p
      style="color: aqua; font-weight: bold; font-style: italic"
      :style="{
        color: redColor,
        fontStyle: noItalic,
        textDecoration: lineUnder,
      }"
    >
      골든차일드 손영택
    </p>

    <hr />
    <h2>클래식 조건에 삼항 연산자 사용하기</h2>
    <p>삼항 연산자 사용할 경우, 배열 리터럴 사용</p>
    <p :class="[isActive ? 'active' : '']">골든차일드 이장준</p>
    <p><button @click="isActive = !isActive">글자 스타일</button></p>

    <hr />
    <h2>객체 데이터 전달하기</h2>
    <p>
      템플릿에 여러 개의 클래스 또는 스타일을 모두 적으면 코드의 가독성이 굉장히
      떨어진다. <br />
      따라서 data 객체에 객체를 정의한 뒤 전달하는 것이 좋다.
    </p>
    <p :class="[classObject ? 'class1' : 'class2']">골든차일드 최성윤</p>
    <p><button @click="classObject = !classObject">스타일 바꾸기</button></p>
    <p :style="styleObject">골든차일드 홍주찬</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      textColor: "green",
      bgColor: "yellow",

      isColor: true,
      isBg: true,
      isBold: true,
      isItalic: false,

      redColor: "red",
      noItalic: "normal",
      lineUnder: "underline",

      isActive: true,

      classObject: { class1: true, class2: false },
      styleObject: {
        color: "red",
        backgroundColor: "yellow",
        "font-weight": "bold",
      },
    };
  },
};
</script>

<style scoped>
.bulColor {
  color: purple;
}
.bg-color {
  background-color: yellow;
}
.bold {
  font-weight: bold;
}
.italic {
  font-style: italic;
}
.active {
  color: yellowgreen;
  font-weight: bold;
}
.class1 {
  color: blue;
  font-weight: bold;
}
.class2 {
  color: aqua;
  font-weight: bold;
}
</style>
