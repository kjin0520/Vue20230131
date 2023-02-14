<template>
  <div>
    <h1>v-else-if, v-else와 key</h1>
    <p>
      v-if, v-else-if, v-else와 같이 디렉티브 내부에 있는 요소의 경우는<br />
      속성의 상태가 남거나 트랜지션이 일어나지 않는 등 예상하지 못한 문제가
      발생할 수 있다.
    </p>
    <p>각각의 요소에 유니크한 key를 설정해 문제를 해결할 수 있다.</p>
    <p>
      key의 역할은 각각의 요소가 다른 요소라는 것을 명시적으로 지정하는 것이다.
    </p>

    <hr />
    <hr />
    <h1>가상 DOM</h1>
    <p>
      가상 DOM은 바인딩한 데이터를 기반으로 만들어지며,<br />
      DOM 노드와 마찬가지로 '가상(VNode) 노드'라고 부르는<br />
      노드로 이루어진 트리 구조를 갖는다.
    </p>
    <ul>
      <li>'데이터 변경'과 '실제 DOM 변경' 처리는 비동기적으로 이루어진다.</li>
      <li>DOM 재사용으로 인해 예측하지 못한 문제가 발생할 수 있다.</li>
    </ul>

    <h2>DOM을 변경하는 시점</h2>
    <p>
      Vue.js는 DOM과 연결된 데이터를 변경하더라도 이를 곧바로 DOM에 반영하지
      않는다.
    </p>
    <p>
      가상 DOM에서 실제 DOM으로 반영되는 것은<br />
      Vue.js의 리액티브 시스템에 의해서 다시 렌더링 처리가 이루어지는
      시점이다.<br />
      따라서 데이터를 변경한 직후에 DOM에 접근해도 반영 전의 상태 그대로이다.
    </p>

    <h2>최적화를 위한 DOM 재사용과 부작용</h2>
    <p>
      Vue.js가 가상 DOM을 사용하는 목적은 렌더링 처리의 성능을 향상시키기
      위함이다.
    </p>
    <p>
      가상 DOM의 차이를 확인하는 알고리즘을 사용해서 렌더링 처리 전에 가상 DOM
      트리에서 변경 대상을 확인하고, 이러한 대상들에만 실제 DOM 노드 추가/ 변경/
      제거 등의 DOM 조작을 실시한다.
    </p>
    <p>
      DOM 조작을 최소한으로 유지하므로 렌더링 성능이 굉장히 좋지만, 이로 인해서
      v-if 등에서 의도하지 않는 결과가 나오는 경우가 있다.
    </p>
    <p>
      toggle의 변경에 의해 렌더링이 바뀌는 경우<br />
      input 요소의 글자는 변경되지 않고 'A'와 'B'라는 글자만 변경된다.<br />
      이는 가상 DOM에서 변경이 없다라고 판단되는 DOM을 재사용하기 때문이다.
    </p>
    <dl>
      <dt><input type="checkbox" v-model="toggle1" /></dt>
      <dd v-if="toggle1">A <input type="text" /></dd>
      <dd v-else>B <input type="text" /></dd>
    </dl>
    <p>
      이와 같은 문제를 막으려면 변경이 필요한 요소 또는 그를 포함하는 요소에 key
      속성을 부여해야 한다. 다음과 같이 input 요소에 key를 설정하면 토글 때 새로
      렌더링 된다.
    </p>
    <dl>
      <dt><input type="checkbox" v-model="toggle2" /></dt>
      <dd v-if="toggle2">A <input type="text" key="a" /></dd>
      <dd v-else>B <input type="text" key="b" /></dd>
    </dl>

    <h2>jQuery등의 DOM 조작 라이브러리와 함께 사용하기</h2>
    <p>
      Vue.js를 사용하면 기본적으로 jQuery와 같은 DOM 조작 계열의 라이브러리를
      같이 사용하지 않아도 된다.
    </p>
    <p>
      DOM을 직접 조작해봤자 데이터가 바뀌지 않는 이상 가상 DOM이 변경되는 것은
      아니기 떄문이다.
    </p>
    <p>DOM 변경은 데이터 바인딩이 기본이다.</p>
    <p>
      만약 DOM에 직접 접근해야 할 필요가 있을 경우<br />
      Vue.js가 제공하는 $el, $refs, 사용자 정의 디렉티브 기능 등을 사용한다.
    </p>
    <p>
      다른 라이브러리와 함께 사용하는 경우에도 <br />
      최대한 Vue.js의 기능을 사용하거나, <br />
      이벤트 버스 또는 Vuex를 조합해서 데이터를 조작하기 바란다.
    </p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      toggle1: true,
      toggle2: true,
    };
  },
};
</script>

<style></style>
