<!--
 * @姓名: 姜润丰
 * @时间: 2020-12-08 22:33:35
 * @功能: 传送门
-->
<template>
  <div>
    <div class="door" v-for="item in list" :key="item" :style="{left: item + 'px'}">
      <img :src="require('./../assets/gonext.png')">
    </div>
  </div>
</template>
<script>
export default {
  name: "trans",
  props: {
    list: {
      type: Array,
      default: () => { return [] }
    }
  }
}
</script>
<style lang="scss" scoped>
.door {
  width: 120px;
  overflow: hidden;
  display: flex;
  position: absolute;
  opacity: 0.8;
  img {
    transform: translateX(-25px);
    animation: run 5s infinite;
  }
  @keyframes run {
    0% {
      transform: scale(1);
    }
    50% {
      transform: scale(0.9);
    }
    100% {
      transform: scale(1);
    }
  }
}
</style>
