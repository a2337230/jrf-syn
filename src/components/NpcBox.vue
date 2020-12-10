<!--
 * @姓名: 姜润丰
 * @时间: 2020-12-08 22:33:35
 * @功能: NPC
-->
<template>
  <div class="npcs">
    <div class="npc-item" v-for="(item, index) in NpcSetting" :key="index" :style="{'margin-right': item.mr + 'px', 'margin-bottom': item.bottom ? item.bottom + 'px' : ''}">
      <div class="dialog" v-if="item.width" :style="item | styleFormat">{{item.text}}</div>
      <img :src="item.icon" class="people">
      <p class="npc-name" v-if="item.nameShow">{{item.name}}</p>
    </div>
  </div>
</template>
<script>
export default {
  name: 'npc',
  props: {
    NpcSetting: {
      type: Array,
      default: () => { return [] }
    }
  },
  filters: {
    styleFormat(val) {
      let style = ""
      if (val.width < 120) {
        style = `left:-${(120 - val.width) / 2}px;bottom:${val.height + 30}px;`
      } else {
        style = `left:${(val.width - 120) / 2}px;bottom:${val.height + 30}px;`
      }
      return style
    }
  }
}
</script>
<style lang="scss" scoped>
.npcs {
  display: flex;
  align-items: flex-end;
  position: relative;
  padding-left: 20px;
  .npc-item {
    position: relative;
    display: flex;
    justify-content: center;
    .dialog {
      position: absolute;
      width: 120px;
      min-height: 50px !important;
      box-sizing: border-box;
      padding: 10px;
      display: flex;
      align-items: center;
      font-size: 14px;
      color: #880000;
      word-break: break-all;
      background: linear-gradient(#f6f7f9, #d6d8dc) 0 50%;
      border-radius: 10px;
      border: 1px solid #000;
      text-shadow: 0 1px hsl(0,0%,85%),0 2px hsl(0,0%,80%),0 3px hsl(0,0%,75%),0 5px 30px #bbb;
      box-shadow: 1px 1px 0 0 rgba(255, 255, 255, 0.15) inset, 0 0 0 0 transparent inset, 0.2em 0.2em 0.3em -0.07em rgba(255, 255, 255, 0.6) inset, -0.2em -0.3em 0.3em -0.07em rgba(0, 0, 0, 0.08) inset;
      &::after {
        content:'';
        position:absolute;
        top:100%;
        left:50%;
        margin-left: -15px;
        width:77px;
        height:20px;
        border-width:0;
        border-style:solid;
        border-color:transparent;
        margin-top:-2px;
        border-left-width:14px;
        border-left-color:#000;
        border-radius:0 0 0 154px;
        z-index: 2;
      }
      &::before {
        content:'';
        position:absolute;
        top:100%;
        left:50%;
        margin-left: -14px;
        width:77px;
        height:20px;
        border-width:0;
        border-style:solid;
        border-color:transparent;
        margin-top:-2px;
        border-left-width:12px;
        border-left-color:rgb(216, 216, 216);
        border-radius:0 0 0 154px;
        z-index: 3;
      }
    }
    .npc-name {
      position: absolute;
      height: 20px;
      bottom: -25px;
      z-index: 55;
      color: #ffff00;
      background-color: rgba(0,0,0,0.7);
      padding: 0 5px;
      font-size: 14px;
      line-height: 20px;
      border-radius: 3px;
    }
  }
  
}
</style>