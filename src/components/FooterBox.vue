<!--
 * @姓名: 姜润丰
 * @时间: 2020-12-08 22:33:35
 * @功能: 底部信息栏
-->
<template>
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
      <img :src="require('./../assets/js.png')">
      <!-- 宝具 -->
      <img :src="require('./../assets/wq.png')">
      <!-- 行囊 -->
      <img :src="require('./../assets/xn.png')">
      <!-- 人物 -->
      <img :src="require('./../assets/rw.png')">
      <!-- 强化 -->
      <img :src="require('./../assets/qh.png')">
      <!-- 日常 -->
      <img :src="require('./../assets/rc.png')">
      <!-- 奖励 -->
      <img :src="require('./../assets/jl.png')">
      <!-- 社交 -->
      <img :src="require('./../assets/sj.png')">
      <!-- 修炼 -->
      <img :src="require('./../assets/xl.png')">
      <!-- 观星 -->
      <img :src="require('./../assets/gx.png')">
      <!-- 设置 -->
      <img :src="require('./../assets/sz.png')">
    </div>
  </div>
</template>
<script>
export default {
  name: 'footer-box',
  data() {
    return {
      // 段位
      level: [
        {
          text: "HTML",
          icon: require('./../assets/lv1.png'),
          min: 1,
          max: 29
        },
        {
          text: "CSS",
          icon: require('./../assets/lv2.png'),
          min: 30,
          max: 59
        },
        {
          text: "JS",
          icon: require('./../assets/lv3.png'),
          min: 60,
          max: 89
        },
        {
          text: "VUE",
          icon: require('./../assets/lv4.png'),
          min: 90,
          max: 120
        }
      ]
    }
  },
}
</script>
<style lang="scss" scoped>
.user-info {
  height: 40px;
  position: fixed;
  width: 100vw;
  height: 50px;
  bottom: 30px;
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
      text-shadow: 1px 1px rgb(153, 148, 148),2px 2px rgb(153, 148, 148),3px 3px rgb(153, 148, 148),4px 4px rgb(153, 148, 148),5px 5px rgb(153, 148, 148),5px 5px 30px rgb(153, 148, 148);
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
</style>