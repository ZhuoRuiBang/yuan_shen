<template>
  <!-- 导航栏 -->
  <div class="nav">
    <div class="left">
      <a href="javascript:;" class="nav_logo">
        <img src="../assets/images/music_open.png" alt="logo" />
      </a>
      <div class="list" @mouseleave="eventLave($event)">
        <ul>
          <li
            v-for="(item, index) of navs"
            :key="item.title"
            :class="{ active: item.isActive }"
            @mouseenter="eventMve(index, $event)"
          >
            {{ item.title }}
          </li>
        </ul>
        <div ref="move" class="move"></div>
      </div>
    </div>
    <div class="right">
      <a href="javascript:;">
        <span>成长关爱系统</span>
        <img src="../assets/images/love.png" alt="" />
      </a>
      <a class="login" href="javascript:;">
        <span>登&nbsp;录</span>
        <img src="../assets/images/user.png" alt="" />
      </a>
    </div>
  </div>
</template>

<script setup>
import { ref, reactive } from "vue";
const navs = reactive([
  { title: `首 页`, isActive: true },
  { title: "新 闻", isActive: false },
  { title: "角 色", isActive: false },
  { title: "世 界", isActive: false },
  { title: "漫 画", isActive: false },
  { title: "社 区", isActive: false },
  { title: "赛 事", isActive: false },
]);
let offsetMove = ref(0);
const move = ref(); //获取光标元素

// 移动光标
function eventMve(index, e) {
  offsetMove.value = index * (60 + e.target.clientWidth) + 30; //单个li的总宽度
  move.value.style.left = `${offsetMove.value}px`;
}
// 鼠标离开，光标回到选中的位置
function eventLave(e) {
  //获取光标元素
  navs.forEach((item, index) => {
    if (item.isActive === true) {
      offsetMove.value = index * (60 + e.target.clientWidth) + 30; //单个li的总宽度
      move.value.style.left = `${offsetMove.value}px`;
    }
  });
}
</script>

<style lang="less" scoped>
.nav {
  position: fixed;
  top: 0;
  left: 0;
  min-width: 1280px;
  display: flex;
  width: 100%;
  height: 66px;
  background-color: rgba(17, 17, 17, 0.75);
  box-shadow: 0px 3px 7px 0px rgba(0, 0, 0, 0.35);
  justify-content: space-between;
  color: #ccc;
  z-index: 1;

  .left {
    .nav_logo {
      display: inline-block;
      margin-left: 8px;
      margin-right: 0px;
      width: 233px;
      height: 100%;
      background: transparent
        url(https://ys.mihoyo.com/main/_nuxt/img/logo-header-cut.f78aabc.png) no-repeat 0
        0;
      cursor: pointer;

      img {
        width: 30px;
        height: 30px;
        cursor: pointer;
        position: fixed;
        top: 18px;
        left: 70px;
      }
    }

    .list {
      position: relative;
      display: inline-block;
      margin-left: 40px;

      li {
        float: left;
        line-height: 66px;
        margin: 0 30px;
        font-size: 17px;
        text-align: center;
        cursor: pointer;
        &:hover {
          text-shadow: 0 0 10px #69e0ff, 0 0 20px #69e0ff, 0 0 40px #69e0ff;
          color: #fff;
        }
      }

      .move {
        position: absolute;
        z-index: 1;
        transition: all 0.2s ease-in-out 0s;
        background-color: rgb(105, 224, 255);
        height: 5px;
        left: 30px;
        width: 40px;
        top: 0px;
      }
    }
  }

  .right {
    position: absolute;
    right: 30px;
    top: 0;
    height: 100%;
    display: flex;
    align-items: center;
    .login{
      padding: 0 10px;
      margin-right: 0;
    }
    a {
      display: flex;
      margin-right: 20px;
      align-items: center;

      span {
        font-size: 17px;
      }

      img {
        margin-left: 18px;
        width: 27px;
        height: 27px;
        opacity: 0.6;
      }

      &:hover {
        img {
          opacity: 1;
        }

        span {
          color: #fff;
        }
      }
    }
  }
}
</style>
