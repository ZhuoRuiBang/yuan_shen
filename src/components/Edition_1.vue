<template>
  <!-- 首页第一版 -->
  <div class="edition_1">
    <!-- 背景图 -->
    <div class="bg">
      <video
        src="https://ys.mihoyo.com/main/_nuxt/videos/bg.3e78e80.mp4"
        loop="loop"
        muted="muted"
        autoplay
        ref="video"
      ></video>
    </div>
    <div class="content">
      <!-- 七圣召唤 -->
      <div class="qisheng">
        <img src="https://ys.mihoyo.com/main/_nuxt/img/pc.90a8b69.png" alt="" />
      </div>
      <!-- 版本信息 -->
      <div class="ys-download__txts">
        <p class="txt1">应用名称：原神</p>
        <p class="txt2">开发者名称：上海米哈游天命科技有限公司</p>
        <p class="txt3">
          <span>当前版本：4.3.0</span>
          <span>更新时间：2023.12.20</span>
        </p>
        <p class="txt4">
          <a href="https://ys.mihoyo.com/main/m/company/privacy">隐私协议</a>
          <a href="https://ys.mihoyo.com/main/m/news/detail/13367"
            >产品功能及用户权限</a
          >
        </p>
      </div>
      <!-- 播放按钮 -->
      <div class="play_video">
        <button>播放</button>
      </div>
      <!-- 下载专区 -->
      <div class="main">
        <div class="download">
          <!-- 二维码 -->
          <div class="download_qr">
            <img src="../assets/images/logo.jpeg" alt="" />
            <img src="../assets/images/qr.png" alt="" />
          </div>
          <!-- 云原神 -->
          <div class="pc_ys">
            <a
              href="https://ys.mihoyo.com/cloud/?autobegin=1&utm_source=default"
            >
              <img src="../assets/images/cloud_ys.png" alt="" />
              <img src="../assets/images/cloud_ys_hover.png" alt="" />
            </a>
          </div>
          <!-- PS4、苹果下载 -->
          <div class="download_group">
            <a
              href="https://ys-api.mihoyo.com/event/download_porter/link/ys_cn/official/ps4_default"
            >
              <img src="../assets/images/ps4.png" alt="ps4" />
              <img src="../assets/images/ps4_hover.png" alt="ps4" />
            </a>
            <a
              href="https://ys-api.mihoyo.com/event/download_porter/link/ys_cn/official/ios_default"
            >
              <img src="../assets/images/ios.png" alt="ios" />
              <img src="../assets/images/ios_hover.png" alt="ios" />
            </a>
          </div>
          <!-- TapTap、安卓下载 -->
          <div class="download_group">
            <a
              href="https://ys-api.mihoyo.com/event/download_porter/link/ys_cn/official/taptappc_default"
            >
              <img src="../assets/images/taptap.png" alt="taptap" />
              <img src="../assets/images/taptap_hover.png" alt="" />
            </a>
            <a
              href="https://ys-api.mihoyo.com/event/download_porter/link/ys_cn/official/android_default"
            >
              <img src="../assets/images/android.png" alt="taptap" />
              <img src="../assets/images/android_hover.png" alt="" />
            </a>
          </div>
          <!-- pc下载 -->
          <div class="download_pc">
            <a
              href="https://ys-api.mihoyo.com/event/download_porter/link/ys_cn/official/pc_default"
            >
              <img src="../assets/images/pc.png" alt="" />
              <img src="../assets/images/pc_hover.png" alt="" />
            </a>
          </div>
        </div>
      </div>
      <div class="down">
        <div></div>
        <div></div>
        <div></div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref,onMounted} from 'vue';
const video = ref();
onMounted(() => {
  video.value.style.width =`${window.innerWidth}px`
  video.value.style.height =`${window.innerHeight}px`
})
</script>

<style lang="less" scoped>
.hover {
  a {
    &:hover img:first-child {
      display: none;
    }
    &:hover img:last-child {
      display: block;
    }
    img {
      &:first-child {
        display: block;
      }
      &:last-child {
        display: none;
      }
    }
  }
}
.edition_1 {
  position: relative;
  .bg {
    position: relative;
    width: 100%;
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    overflow: hidden;
    video {
      object-fit: cover;
    }
  }
  .qisheng {
    position: absolute;
    width: 161px;
    height: 152px;
    top: 71px;
    right: 28px;
    z-index: 6;
    img {
      width: 100%;
      height: auto;
      cursor: pointer;
    }
  }
  .ys-download__txts {
    position: absolute;
    bottom: 20px;
    left: 20px;
    color: #fff;
    font-size: 16px;
    line-height: 24px;
    .txt3 span:last-child {
      margin-left: 5px;
    }
    .txt4 a {
      color: #fff;
      text-decoration: underline;
      &:last-child {
        margin-left: 25px;
      }
    }
  }
  .content {
    display: flex;
    position: absolute;
    left: 0;
    top: 0;
    right: 0;
    bottom: 0;
    flex-direction: column;
    align-items: center;
    justify-content: flex-end;
    .play_video {
      width: 356px;
      height: 76px;
      background: url("../assets/images/play_bg.png") no-repeat center center;
      margin-bottom: 20px;
      button {
        position: relative;
        display: block;
        margin: 14px auto 0;
        width: 48px;
        height: 48px;
        border-radius: 50%;
        border: 0;
        background: #fff;
        font-size: 0;
        cursor: pointer;
        outline: none;
        transition: background 0.2s linear;
        &:hover {
          background: transparent;
          &::before {
            background-position: center bottom;
          }
        }
        &::before {
          content: "";
          display: block;
          position: absolute;
          left: 50%;
          top: 50%;
          z-index: 1;
          width: 28px;
          height: 28px;
          transform: translate(-50%, -50%);
          background: url("../assets/images/play.png") no-repeat;
          background-position: center top;
        }
      }
    }
    .main {
      flex-shrink: 0;
      margin-bottom: 20px;
      height: 125px;
      .download {
        display: flex;
        justify-content: space-between;
        margin: 0 auto;
        width: 622px;
        height: 100%;
        align-items: center;
        a {
          display: block;
          cursor: pointer;
          flex-shrink: 0;
        }
        img {
          width: 100%;
          height: 100%;
          object-fit: cover;
        }
        .download_qr {
          position: relative;
          width: 94px;
          height: 94px;
          img:first-child {
            position: absolute;
            left: 50%;
            top: 33px;
            transform: translateX(-50%);
            z-index: 1;
            width: 30px;
            height: 30px;
            border: 2px solid #475e7d;
            border-radius: 4px;
          }
          img:last-child {
            width: 100%;
            display: block;
          }
        }
        .pc_ys {
          .hover();
        }
        .download_group {
          display: flex;
          flex-direction: column;
          justify-content: space-between;
          align-items: center;
          height: 95px;
          a {
            width: 155px;
            height: 44px;
          }
          .hover();
        }
        .download_pc {
          a {
            width: 95px;
            height: 95px;
          }
          .hover();
        }
      }
    }
    .down {
      position: relative;
      margin-bottom: 13px;
      width: 25px;
      div {
        width: 100%;
        height: 15px;
        background: url("../assets/images/down.png") no-repeat;
        animation: Arrow 1.5s infinite linear;
      }
    }
  }
}
</style>