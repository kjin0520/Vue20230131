<template>
  <div>
    <h1>조건부 랜더링</h1>
    <p>조건이 참일 때만 출력</p>
    <p>
      조건이 거짓일 때<br />
      v-if는 주석<br />
      v-show는 display:none
    </p>
    <h2>v-if와 v-show의 차이</h2>
    <dl>
      <dt>조건을 만족하지 못한 경우</dt>
      <hr />
      <dt>v-if</dt>
      <dd>
        요소는 DOM 레벨에서 제거<br />
        모든 감시도 제거<br />
        컴포넌트라면 인스턴스가 제거<br />
        이후에 렌더링될 때 모든 상태가 초기화 되어버림
      </dd>

      <dt>v-show</dt>
      <dd>
        단순하게 display:none 사용<br />
        눈에 보이지 않더라도 모든 리액티브 데이터에 대한 내부적인 감시가
        일어난다.
      </dd>
    </dl>

    <hr />

    <dl>
      <dt>
        현재 render1은
        <input type="number" v-model.number="render1" min="1" max="5" />
      </dt>
      <dd v-if="render1 === 1">{{ render1 }} 최저 점수입니다.</dd>
      <dd v-else-if="render1 === 5">{{ render1 }} 최고 점수 입니다.</dd>
      <dd v-else>{{ render1 }}입니다.</dd>
      <dt>현재 render2는<input type="checkbox" v-model="render2" /></dt>
      <dd v-show="render2">{{ render2 }} 입니다.</dd>
      <dd v-show="!render2">{{ render2 }} 입니다.</dd>
    </dl>

    <hr />
    <h2>v-if와 v-show의 적절한 사용방법</h2>
    <dl>
      <dt>v-if와 v-show 차이는 실제로 요소가 존재하느냐의 여부</dt>
      <dd>
        내부에서 디렉티브 또는 컴포넌트를 많이 사용하는 경우,<br />
        특정한 데이터를 따로 가지고 있지 않다면<br />
        v-if를 사용하는 것이 좋다.
      </dd>
      <dd>
        내부에 디렉티브 또는 컴포넌트가 없고<br />
        변경 빈도가 높은 경우 v-show를 사용하는 것이 좋다.
      </dd>
      <dt>결론</dt>
      <dd>
        자주 바뀌는 화면이 아니라면 v-if는 요소를 만들지 않아서 사용하는 자원이
        적어지므로 더 유리할 수 있다.
      </dd>
      <dd>
        자주 바뀌는 화면에서는 v-show를 사용하는 편이 자원을 덜 사용하게 된다.
      </dd>
    </dl>
  </div>
</template>

<script>
export default {
  data() {
    return {
      render1: 1,
      render2: true,
    };
  },
};
</script>

<style></style>
