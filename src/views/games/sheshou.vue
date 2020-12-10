<!--
 * @姓名: 姜润丰
 * @时间: 2020-12-08 22:33:35
 * @功能: 场景元素-射手村
-->
<template>
  <div class="sheshou">
    <div class="scroll" style="width: 5006px">
      <!-- 天空 -->
      <div class="sky" v-html="sky">
        <!-- <img :src="require('./../../assets/sky.png')" :style="{left: (item - 1) * 10 + '%', top: Math.floor(Math.random()*200+200) - 200 + 'px'}" v-for="item in 10" :key="item"> -->
      </div>
      <!-- 地面 -->
      <div class="pavement">
        <scene-icon :scene="scene['left']"></scene-icon>
        <scene-icon :scene="scene['center']" v-for="item in 50" :key="item"></scene-icon>
        <scene-icon :scene="scene['right']"></scene-icon>
        <div class="nvshen">
          <npc-box :NpcSetting="girl"></npc-box>
        </div>
        <footer-box></footer-box>
        <div class="trans">
          <transfer :list="trans"></transfer>
        </div>
        <!-- 附属物 -->
        <div class="adjunct">
          <npc-box :NpcSetting="npc"></npc-box>
        </div>
      </div>
    </div>
    
    <!-- <audio id="music" :src="require('./../../music/smcbj.mp3')" preload loop controls></audio> -->
  </div>
</template>
<script>
// NPC
import NpcBox from "@/components/NpcBox"
// 底部信息栏
import FooterBox from "@/components/FooterBox"
// 路面拼图
import SceneIcon from '@/components/SceneIcon'
// 传送门
import Transfer from '@/components/Transfer'
// npc信息
import { Npc } from '@/utils/npc'
export default {
  name: 'sheshou',
  components: {
    SceneIcon,
    FooterBox,
    NpcBox,
    Transfer
  },
  data() {
    return {
      // 天空
      sky: "",
      // 路面左
      scene: {
        left: [128, 128, -448, -193],
        center: [95, 128, -609, -193],
        right: [128, 128, -740, -193]
      },
      // 路面
      bottom: ["left", "center", "right"],
      // NPC
      npc: [],
      // 女神
      girl: [
        {
          width: 300,
          height: 205,
          name: "程序猿的渴望",
          icon: require('@/assets/nvshen.png'),
          mr: 40,
          nameShow: true,
          text: "每个程序猿心中都藏着一个女神我就是你的动力"
        }
      ],
      // 传送门位置
      trans: [1200, 2380,2840, 3230,3620, 4200]
    }
  },
  created() {
    let cloud = ""
    for(let i = 1; i < 10; i++) {
      cloud+=`<img src="${require('./../../assets/sky.png')}" style="left: ${(i - 1) * 10}%; top:${Math.floor(Math.random()*200+200) - 200}px;position: absolute;width: 512px;height: 136px;">`
    }
    this.sky = cloud
    this.npc = Npc.sheshou
  },
  mounted() {
    // let music = document.getElementById('music')
    // music.addEventListener("canplay", (e) => {//监听audio是否加载完毕，如果加载完毕，则读取audio播放时间
    //   console.log('mp3加载完成............', e, music)
    //   music.play()
    //   // that.loading = false;
    // });
  },
  methods: {
    mouseShow(val, boolean) {
      this.dialog[val] = boolean
    }
  }
}
</script>
<style lang="scss" scoped>
.sheshou {
  width: 100vw;
  .scroll {
    height: 100vh;
    position: relative;
    transform: translateX(-3500px);
  }
  .sky {
    width: 100vw;
    position: absolute;
    left: 0;
    top: 0;
    display: flex;
    img {
      position: absolute;
      width: 512px;
      height: 136px;
    }
  }
  .adjunct {
    position: absolute;
    bottom: 122px;
    display: flex;
    .my {
      margin-left: 50px;
      margin-right: 30px;
    }
    .dialog {
      position: absolute;
      width: 200px;
      height: 120px;
      display: flex;
      p {
        position: relative;
        z-index: 2;
        top: 25px;
        width: 100%;
        padding: 0 10px;
        box-sizing: border-box;
        text-align: center;
        line-height: 24px;
      }
      img {
        position: absolute;
        width: 200px;
        height: 120px;
      }
    }
    .name {
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
    .dog-home {
      position: relative;
      width: 108px;
      margin-right: 50px;
      display: flex;
      justify-content: center;
      .dialog {
        top: -70px;
        left: -100px;
      }
    }
    .my-doctor {
      position: relative;
      width: 108px;
      margin-right: 50px;
      display: flex;
      justify-content: center;
      .dialog {
        top: -70px;
        left: -100px;
      }
    }
  }
  .pavement {
    position: absolute;
    display: flex;
    left: 0;
    bottom: 0;
    .nvshen {
      position: absolute;
      left: 30px;
      top: -600px;
      animation: move 3s infinite linear;
    }
    @keyframes move {
      0% {
        top: -600px
      }
      50% {
        top: -580px
      }
      100% {
        top: -600px
      }
    }
    .trans {
      height: 183px;
      position: absolute;
      bottom: 105px;
      left: 0;
      z-index: 2;
    }
  } 
}
.b0 {
  position: absolute;
  bottom: 0;
}
</style>