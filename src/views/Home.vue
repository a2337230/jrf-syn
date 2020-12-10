<!--
 * @姓名: 姜润丰
 * @时间: 2020-12-08 22:33:35
 * @功能: 主页面,用户加载各种关卡
 * @路径: \maoxian_demo\src\views\Home.vue
-->
<template>
  <div class="home">
    <sheshou></sheshou>
  </div>
</template>
<script>
import sheshou from "./games/sheshou";
export default {
  name: "Home",
  components: {
    sheshou,
  },
  data() {
    return {
      // 关卡切换
      gameTabs: "射手"
    };
  },
};
</script>
<style lang="scss" scoped>
.home {
  width: 100vw;
  height: 100vh;
  overflow: hidden;
}
</style>
