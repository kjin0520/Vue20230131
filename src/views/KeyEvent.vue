<template>
  <div>
    <h1>Key</h1>
    <p>
      keyup, keydown, keypress 중 keyup을 가장 많이 쓰게 된다.그 이유는
      입력값까지 받아낼 수 있기 떄문이다.
    </p>
    <p>
      <input type="text" @keyup="handlKeyEvent1('keyup', $event)" />
      keyup
    </p>

    <p>
      <input type="text" @keydown="handlKeyEvent1('keydown', $event)" />
      keydown
    </p>

    <p>
      <input type="text" @keypress="handlKeyEvent1('keypress', $event)" />
      keypress
    </p>

    <hr />
    <hr />
    <h2>사용할 수 있는 키 코드 별칭</h2>
    <p>
      .enter <br />
      .tab <br />
      .delete<br />
      .esc<br />
      .space<br /><br />
      .up<br />
      .down <br />
      .left<br />
      .right
    </p>
    <p>
      <input type="text" @keyup.enter="handlKeyEvent('enter', $event)" />
      Enter 키를 눌렀을 때
      <input type="text" @keyup.tab="handlKeyEvent2('tab')" />
      tab 키를 눌렀을 때
      <input type="text" @keyup.delete="handlKeyEvent2('delete')" />
      delete 키를 눌렀을 때
      <input type="text" @keyup.esc="handlKeyEvent2('esc')" />
      esc 키를 눌렀을 때
      <input type="text" @keyup.space="handlKeyEvent2('space')" />
      space 키를 눌렀을 때
      <input type="text" @keyup.up="handlKeyEvent2('up')" />
      up 키를 눌렀을 때
      <input type="text" @keyup.down="handlKeyEvent2('down')" />
      down 키를 눌렀을 때
      <input type="text" @keyup.left="handlKeyEvent2('left')" />
      left 키를 눌렀을 때
      <input type="text" @keyup.right="handlKeyEvent2('right')" />
      right 키를 눌렀을 때
    </p>

    <hr />
    <p>
      <input
        type="text"
        @keyup.up.down.left.right="handlKeyEvent2($event.key)"
      />
    </p>
    <p>여러 개의 키 코드를 붙여서 입력하면 'OR'을 의미한다.</p>

    <hr />
    <hr />
    <h2>시스템 장식자</h2>
    <p>시스템 장식자는 대응하는 키가 눌린 경우에만 핸들러 호출</p>
    <p>
      .ctrl <br />
      .alt <br />
      .shift <br />
      .meta <br />
    </p>
    <p>
      <input type="text" @keyup.ctrl.enter="handlKeyEvent2('ctrl.enter입력')" />
      복합키 입력
    </p>
  </div>
</template>

<script>
export default {
  data() {
    return {};
  },
  methods: {
    handlKeyEvent1(evnetName, e) {
      console.log(evnetName, e.target.value);
    },
    handlKeyEvent2(evnetName) {
      console.log(evnetName);
    },
  },
};
</script>

<style></style>
