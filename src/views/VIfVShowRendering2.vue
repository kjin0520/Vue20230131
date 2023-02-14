<template>
  <div>
    <h1>template태그를 사용한 v-if 그룹</h1>
    <p>v-if는 단일 요소에 적용해야 한다.</p>
    <p>
      여러 요소에 같은 조건을 부여할 떄는 template 태그를 사용하여<br />여러
      요소를 그룹으로 만들 수 있다.
    </p>
    <p>v-show로는 할 수 없다.</p>
    <template v-if="ok">
      <header>타이틀</header>
      <div>콘텐츠</div>
    </template>
  </div>
</template>

<script>
export default {
  data() {
    return {
      ok: true,
    };
  },
};
</script>

<style></style>
