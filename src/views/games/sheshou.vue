<!--
 * @姓名: 姜润丰
 * @时间: 2020-12-08 22:33:35
 * @功能: 场景元素-射手村
-->
<template>
  <div class="sheshou">
    <!-- 天空 -->
    <div class="sky" v-html="sky">
      <!-- <img :src="require('./../../assets/sky.png')" :style="{left: (item - 1) * 10 + '%', top: Math.floor(Math.random()*200+200) - 200 + 'px'}" v-for="item in 10" :key="item"> -->
    </div>
    <!-- 附属物 -->
    <div class="adjunct">
      <img :src="require('./../../assets/my.png')" class="my">
      <div class="dog-home">
        <div class="dialog" v-if="dialog.dogHome">
          <p>我的主人是一名<br>前端工程师</p>
          <img :src="require('./../../assets/bubb.png')">
        </div>
        <img :src="require('./../../assets/dog.png')" class="my-dog b0" @mouseenter="mouseShow('dogHome', true)" @mouseleave="mouseShow('dogHome', false)">
        <p class="name">MINI</p>
      </div>
      <div class="my-doctor">
        <div class="dialog" v-if="dialog.doctor">
          <p>我是蘑菇博士<br>点击我查看主人信息哦</p>
          <img :src="require('./../../assets/bubb.png')">
        </div>
        <img :src="require('./../../assets/myspk.gif')" class="my-spk b0 item-click" @mouseenter="mouseShow('doctor', true)" @mouseleave="mouseShow('doctor', false)">
        <p class="name">蘑菇博士</p>
      </div>
    </div>
    <!-- 地面 -->
    <div class="pavement">
      <scene-icon :scene="scene['left']"></scene-icon>
      <scene-icon :scene="scene['center']" v-for="item in 50" :key="item"></scene-icon>
      <scene-icon :scene="scene['right']"></scene-icon>
      <div class="user-info">
        <div class="user-name">
          <p class="user-lv">LV. 151</p>
          <div class="user-des">
            <p class="job">前端工程师</p>
            <p class="pet">姜润丰</p>
          </div>
          <div class="stage">
            <img :src="level[0].icon">
          </div>
        </div>
        <div class="expend">
          <div class="top">
            <div class="hp">
              <span class="text">HP.</span>
              <div class="expend-box">
                <div class="bar" style="width: 50%"></div>
              </div>
            </div>
            <div class="mp">
              <span class="text">MP.</span>
              <div class="expend-box">
                <div class="bar" style="width: 50%"></div>
              </div>
            </div>
          </div>
          <div class="exp">
            <span class="text"> EXP.</span>
            <div class="expend-box">
              <div class="bar" style="width: 50%"></div>
            </div>
          </div>
        </div>
        <div class="fun-btn">
          <!-- 人物 -->
          <img :src="require('./../../assets/js.png')">
          <!-- 宝具 -->
          <img :src="require('./../../assets/wq.png')">
          <!-- 行囊 -->
          <img :src="require('./../../assets/xn.png')">
          <!-- 人物 -->
          <img :src="require('./../../assets/rw.png')">
          <!-- 强化 -->
          <img :src="require('./../../assets/qh.png')">
          <!-- 日常 -->
          <img :src="require('./../../assets/rc.png')">
          <!-- 奖励 -->
          <img :src="require('./../../assets/jl.png')">
          <!-- 社交 -->
          <img :src="require('./../../assets/sj.png')">
          <!-- 修炼 -->
          <img :src="require('./../../assets/xl.png')">
          <!-- 观星 -->
          <img :src="require('./../../assets/gx.png')">
          <!-- 设置 -->
          <img :src="require('./../../assets/sz.png')">
        </div>
      </div>
    </div>
    <!-- <audio id="music" :src="require('./../../music/smcbj.mp3')" preload loop controls></audio> -->
  </div>
</template>
<script>
import SceneIcon from '@/components/SceneIcon'
export default {
  name: 'sheshou',
  components: {
    SceneIcon
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
      // 对话
      dialog: {
        dogHome: false,
        doctor: false
      },
      // 段位
      level: [
        {
          text: "HTML",
          icon: require('./../../assets/lv1.png'),
          min: 1,
          max: 29
        },
        {
          text: "CSS",
          icon: require('./../../assets/lv2.png'),
          min: 30,
          max: 59
        },
        {
          text: "JS",
          icon: require('./../../assets/lv3.png'),
          min: 60,
          max: 89
        },
        {
          text: "VUE",
          icon: require('./../../assets/lv4.png'),
          min: 90,
          max: 120
        }
      ]
    }
  },
  created() {
    let cloud = ""
    for(let i = 1; i < 10; i++) {
      cloud+=`<img src="${require('./../../assets/sky.png')}" style="left: ${(i - 1) * 10}%; top:${Math.floor(Math.random()*200+200) - 200}px;position: absolute;width: 512px;height: 136px;">`
    }
    this.sky = cloud
    console.log(cloud)
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
      console.log(this.dialog)
    }
  }
}
</script>
<style lang="scss" scoped>
.sheshou {
  width: 100vw;
  height: 100vh;
  position: relative;
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
    bottom: 126px;
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
    position: fixed;
    display: flex;;
    // left: -28px;
    // bottom: -28px;
    bottom: 0;
    .user-info {
      height: 40px;
      position: absolute;
      width: 100vw;
      height: 50px;
      bottom: 30px;
      // background-image: linear-gradient(to top, #D8D9DB 0%, #fff 80%, #FDFDFD 100%);
      // box-shadow: 4px 0px 3px 3px #FCFCFC;
      display: flex;
      align-items: center;
      .user-name {
        width: 15%;
        min-width: 270px;
        height: 48px;
        background: -webkit-gradient(linear, left top, left bottom, from(#888), to(#575757));
        margin-left: 5px;
        border-radius: 5px;
        display: flex;
        align-items: center;
        .user-lv {
          font-size: 30px;
          color: #fbd125;
          padding-left: 10px;
        }
        .user-des {
          margin-left: 10px;
          p {
            font-size: 14px;
            color: #fff;
          }
          .job {
            color: #fbd125;
          }
        }
        .stage {
          width: 40px;
          height: 40px;
          background-color: #fff;
          margin-left: 20px;
          display: flex;
          justify-content: center;
          align-items: center;
          background-image: linear-gradient(to top, #D8D9DB 0%, #fff 80%, #FDFDFD 100%);
          border-radius: 30px;
          border: 1px solid #8F9092;
          box-shadow: inset 0 0 3px 0 #CECFD1;
          .current {

          }
        }
      }
      .expend {
        width: 35%;
        min-width: 400px;
        padding: 0 10px;
        box-sizing: border-box;
        .top {
          display: flex;
        }
        .hp,.mp {
          height: 20px;
          width: 50%;
          display: flex;
          margin-bottom: 5px;
          .bar {
            height: 100%;
          }
        }
        .hp .bar {
          background-image: linear-gradient(#ffbcce,#e70034, #ffbcce);
        }
        .mp .bar {
          background-image: linear-gradient(#9ae9fa,#0fb9e2, #9ae9fa);
        }
        .exp {
          height: 20px;
          width: 100%;
          display: flex;
          .bar {
            height: 100%;
            background-image: linear-gradient(#eeffc0,#8fc609, #eeffc0);
          }
        }
        .expend-box {
          flex: 1;
          height: 100%;
          background-image: linear-gradient(#b9b9b9,#404040, #b9b9b9);
          margin: 0 10px;
          border-radius: 5px;
          overflow: hidden;
          border: 2px solid #4b4950;
          box-sizing: border-box;
        }
        .text {
          width: 2em;
          font-size: 14px;
          font-weight: bold;
          color: #fff;
          text-shadow: 0.2em 0.2em 0.2em black, 0em -0.2em 0.2em black,-0.2em 0em 0.2em black;
        }
      }
      .fun-btn {
        width: 50%;
        min-width: 500px;
        box-sizing: border-box;
        text-align: right;
        white-space: nowrap;
        img {
          width: 80px;
          height: 80px;
          transition: .2s linear;
          transform: scale(1);
          &:hover {
            transform: scale(1.1);
          }
        }
      }
    }
  } 
}
.b0 {
  position: absolute;
  bottom: 0;
}
</style>