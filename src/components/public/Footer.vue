<template>
  <div class="footer_container" :style="footerHeight + 'px'">
    <div class="footer_content">
      <div class="footer_logo footer-content-column">
        <!--        <div class="logo-container">
                  <img :src="logo_url" alt="">
                  <div class="logo-text">
                    <p class="text1">Xanadu</p>
                    <p class="text2">INTERNET COMPANY</p>
                  </div>
                </div>-->
        <h2><b>湛江市博瑞机械设备有限公司</b></h2>
        <h2>Copyright (c) 2021 AeroWang</h2>
        <h2>运维:guiyi_ac 1677852098@qq.com</h2>
        <br>
        <!--<h2>粤ICP备2024193819号-1</h2>-->
        <a class="img_beian" href="https://beian.miit.gov.cn/" target="_blank">粤ICP备2024193819号-1</a>
        <br>
        <!--<h2>X公网安备 xxxxxxxxxxxxxx号</h2>-->
        <img class="img_beian" src="../../assets/img/beian.png" alt="备案图标">
        <a href="https://beian.mps.gov.cn/#/query/webSearch?code=44080302000223" rel="noreferrer" target="_blank">
          粤公网安备44080302000223</a>
      </div>
      <!--      <div class="about_us footer-content-column">
              <h2>关于我们</h2>
              <ul class="about_list">
                <li>
                  <router-link to="/job" target="_blank">企业文化</router-link>
                </li>
              </ul>
            </div>-->
      <!--      <div class="contact_us footer-content-column">
              <h2>联系我们</h2>
              <ul class="contact_list">
                <li v-for="(item, index) in contact_way" :key="index">
                  <a :href="'mailto:' + item.email">{{ item.name }}</a>
                </li>
              </ul>
            </div>-->
      <div class="focus_us footer-content-column">
        <div class="media">
          <!--<h2>联系方式</h2>-->
          <div :class="item.name" v-for="(item, index) in focus_icon" :key="index">
            <el-popover placement="top" trigger="hover">
              <template #reference>
                <div class="qr_popover">
                  <img :src="item.qr" alt="">
                  <h2>{{ item.info }}</h2>
                </div>
              </template>
              <img :src="item.path" :alt="item.name">
            </el-popover>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script lang="ts" setup>
import { onMounted, ref } from 'vue'

type ConcatItem = {
  name: string;
  email: string;
}

type FocusItem = {
  name: string;
  path: NodeRequire;
  qr: NodeRequire;
  info: string;
}

const footerHeight = ref('')
const curWidth = ref('')
const logo_url = ref<any>()
logo_url.value = require('../../assets/img/index/logoColor.png')
const contact_way = ref<ConcatItem[]>([])
const focus_icon = ref<FocusItem[]>([])

onMounted(() => {
    contact_way.value =
      [
        {
          name: '媒体问询',
          email: 'aerowangue@126.com'
        },
        {
          name: '招聘相关',
          email: 'aerowangue@126.com'
        },
        {
          name: '商务合作',
          email: 'aerowangue@126.com'
        },
        {
          name: '广告相关',
          email: 'aerowangue@126.com'

        }]
    focus_icon.value =
      [
        {
          name: 'weibo',
          path: require('../../assets/img/focus/weibo.png'),
          qr: require('../../assets/img/focus/qr_weibo.png'),
          info: '联系电话：13802342910'
        }
        // {
        //   name: 'weixin',
        //   path: require('../../assets/img/focus/weixin.svg'),
        //   qr: require('../../assets/img/focus/qr_weixin.png'),
        //   info: '关注官方微信公众号'
        // },
        // {
        //   name: 'bilibili',
        //   path: require('../../assets/img/focus/bilibili.png'),
        //   qr: require('../../assets/img/focus/qr_bilibili.png'),
        //   info: '关注官方 bilibili 号'
        // }
      ]
  }
)
</script>
<style lang="less" scoped>
* {
  margin: 0;
  padding: 0;
}

h2 {
  font-size: 100%;
  font-weight: 400;
  font-variant: normal;
}

.footer_container {
  width: 100%;
  background: #1f2329;
  padding-bottom: 60px;
}

.footer_content {
  max-width: 1080px;
  color: #fff;
  margin: 50px auto;
  padding: 28px 0 0;
  display: flex;
  flex-direction: row;
  align-items: flex-start;
  height: 50px;

  h2 {
    font-size: 28px;
    line-height: 22px;
    margin: 5px 0;
    color: #7b7e81;
  }

  .footer-content-column {
    flex: 1 1;
    color: #d2d3d4;
    position: relative;
    text-align: center;

    h2 {
      margin-bottom: 18px;
      font-size: 16px;
      font-weight: bold;
    }

    a {
      color: #7B7E8E;
    }

    .about_list,
    .contact_list {
      text-align: center;
      font-size: 14px;
      line-height: 22px;

      li {
        margin-bottom: 15px;
      }

      a {
        color: #d2d3d4;
      }
    }
  }

  .about_us {
    max-width: 202px;
  }

  .contact_us {
    max-width: 202px;
  }

  .focus_us {
    text-align: left;
    padding-left: 10px;

    .media {
      margin-top: 18px;
      display: flex;
      justify-content: space-evenly;
    }

    span {
      margin-right: 18px;
      flex: 0 0 auto;
    }

    h2 {
      text-align: left;
      font-size: 14px;
      font-weight: normal;
      margin-bottom: 4px;
    }
  }

  .footer_logo {
    margin-left: 96px;
    height: 55px;
    text-align: left;
    max-width: 382px;
    min-width: 350px;

    h2 {
      font-size: 14px;
      font-weight: normal;
      margin-bottom: 4px;
    }

    .logo-container {
      display: flex;
      margin-bottom: 9px;

      img {
        height: 50px;
      }

      .logo-text {
        margin-left: 15px;
        position: relative;
        bottom: -6px;
      }

      .text1 {
        font-size: 21px;
        font-weight: bold;
        margin: 0;
      }

      .text2 {
        font-size: 12px;
        margin: 0;
      }
    }
  }
}

@media only screen and (max-width: 991px) {
  .footer_content {
    flex-direction: column;

    .footer-content-column {
      text-align: center;
      margin: 0 auto 0;

      h2 {
        text-align: center;
      }

      padding-left: 0;
    }

    .focus_us div:last-of-type > span {
      margin-right: 0;
    }

    .media {
      justify-content: center;
    }

    .logo-container {
      justify-content: center;
      text-align: left;
    }
  }
}

.qr_popover {
  //  width: 130px;
  //height: 130px;
  text-align: center;

  img {
    width: 80px;
    height: 80px;
    margin-bottom: 10px;
  }

  //margin-left: 30px;
}

.img_beian {
  width: 4%;
}
</style>
