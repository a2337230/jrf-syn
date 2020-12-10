<!--
 * @姓名: 姜润丰
 * @时间: 2020-12-08 22:33:35
 * @功能: 场景拼图素材
-->
<template>
  <div class="scene" :style="boxStyle">
    1
  </div>
</template>
<script>
export default {
  name: "scene",
  props: {
    scene: {
      type: Array,
      default: () => { return [] }
    }
  },
  data() {
    return {
      // 元素坐标
      boxStyle: ""
    }
  },
  created() {
    // 加载元素
    // this.boxStyle = `width:${this.scene['road'][0] + 'px'}`
    this.boxStyle = {
      width: this.scene[0] + 'px',
      height: this.scene[1] + 'px',
      'background-position-x': this.scene[2] + 'px',
      'background-position-y': this.scene[3] + 'px',
    }
  },
}
</script>
<style lang="scss" scoped>
  .scene {
    background: url("./../assets/bg.png");
    background-size: 1024px 1024px;
  }
</style>
