<template>
  <div class="wrap-block">
    <!--    <div class="content-blok service-block">
          <div class="servie-block">
            <div class="block-line"></div>
            <p class="service-info-title">我们服务</p>
            <p class="service-info-subtitle">我们已定制多套解决方案，助您轻松跨入“互联网+”时代</p>
            <div class="service-list">
              <div class="service-title" v-for="(item, index) in serviceList" :key="index">
                <div class="is-hover-shadow">
                  <div class="service-title-shadow ">
                    <img :src="item.path" alt="">
                  </div>
                </div>
                <p class="service-name">{{ item.description }}</p>
              </div>
            </div>
          </div>
        </div>-->
    <div class="content-blok service-idea">
      <div class="service-idea">
        <div class="idea-left">
          <img :src="serviceIdeaImg[0].path" :alt="serviceIdeaImg[0].name">
        </div>
        <div class="idea-right">
          <div class="block-line"></div>
          <p class="idea-title">{{ serviceIdeaInfo.ideaTitle }}</p>
          <!--<p class="idea-subtitle">{{ serviceIdeaInfo.ideaSubTitle }}</p>-->
          <!--<img :src="serviceIdeaImg[1].path" :alt="serviceIdeaImg[1].name">-->
          <p class="idea-desc">{{ serviceIdeaInfo.ideaDesc }}</p>
          <!--<router-link to="/news">-->
          <!--  <el-button type="primary" round>了解更多</el-button>-->
          <!--</router-link>-->
        </div>
      </div>
    </div>
    <!--    <div class="content-blok service-case">
          <div class="service-case">
            <div class="block-line"></div>
            <p class="case-title">我们的服务</p>
            <p class="case-subtitle">我们已定制多套解决方案，助您轻松跨入“互联网+”时代</p>
            <div class="case-list">
              <div class="case-info" v-for="(item, index) in caseList" :key="index">
                <el-card :body-style="{ padding: '0px' }" shadow="hover">
                  <img :src="item.path" :alt="item.desc">
                </el-card>
                <el-progress :percentage="50" :show-text="false"></el-progress>
                <p class="case-desc">{{ item.desc }}</p>
              </div>
            </div>
          </div>
        </div>-->
  </div>
</template>
<script lang="ts" setup name="">
import {onBeforeMount, ref} from 'vue'

// 这里演示一下如何实现复杂类型的定义，使用ts接口继承
interface BaseItem {
  path: string;
}

interface ServiceItem extends BaseItem {
  description: string;
}

interface ImgItem extends BaseItem {
  name: string;
}

interface CaseItem extends BaseItem {
  desc: string;
}

// 其实不用这么复杂，只是演示而已
type InfoData = {
  ideaTitle: string;
  ideaSubTitle: string;
  ideaDesc: string;
}
const serviceList = ref<ServiceItem[]>([])
const serviceIdeaInfo = ref<InfoData>({
  ideaTitle: '公司简介',
  ideaSubTitle: 'SERVICE IDEA',
  ideaDesc: '一、公司概况\n' +
    '      湛江市博瑞机械设备有限公司是专业销售和租赁集装箱搬运设备的企业。  \n' +
    '\n二、主营业务\n' +
    '      公司为用户提供集装箱正面吊、堆高机、叉车等专业的物流设备。销售、租赁、技术支持、配件供应；旧设备回收，二手设备买卖。\n' +
    '\n三、发展状况\n' +
    '      公司人以服务社会、振兴中国物流产业为己任，励精图治，改革创新，开拓进取，经过十余年拼搏，取得了令人瞩目的业绩。展望未来，公司将抓住机遇，加大自主产品创新，加快国际化进程，实现规模经济和跨越式发展，成为具有国际竞争力、国际知名度的中国物流机械旗舰企业，实现“世界一流知名企业”。\n' +
    '\n四、销售网络\n' +
    '      公司在全国各港口、铁路货场、物流基地均有代表处或常驻人员。公司与KCL等多个著名跨国企业建立了密切合作关系，从事代理产品销售，客户开发等业务。'
})
const serviceIdeaImg = ref<ImgItem[]>([])
const caseList = ref<CaseItem[]>([])
const percentage = ref('50')
onBeforeMount(() => {
  serviceList.value = [
    {
      description: '大数据',
      path: require('../assets/img/index/bigData.webp')
    },
    {
      description: '智能多媒体',
      path: require('../assets/img/index/media.webp')
    },
    {
      description: '互联网',
      path: require('../assets/img/index/internet.webp')
    },
    {
      description: '云计算',
      path: require('../assets/img/index/cloud.webp')
    }
  ]
  serviceIdeaImg.value = [
    {
      name: 'lefImg',
      path: require('../assets/img/index/service1.png')
    },
    {
      name: 'rightImg',
      path: require('../assets/img/index/service2.png')
    }
  ]
  caseList.value = [
    {
      desc: '私家智能定制APP',
      path: require('../assets/img/index/app1.jpg')
    },
    {
      desc: '公司业绩统计管理系统',
      path: require('../assets/img/index/system1.jpg')
    },
    {
      desc: '私家智能定制APP',
      path: require('../assets/img/index/app1.jpg')
    },
    {
      desc: '公司业绩统计管理系统',
      path: require('../assets/img/index/system2.jpg')
    }
  ]
})
</script>
<style lang="less" scoped>
.wrap-block {
  position: relative;
  padding-top: 54px;

  .content-block {
    position: relative;
    overflow: hidden;
  }
}

.service-block {
  max-width: 1440px;
  height: 500px;
  margin: 0 auto;
  text-align: center;
  overflow-x: hidden;

  .block-line {
    margin: 0 auto 12px;
    width: 24px;
    height: 4px;
    background-color: #3370ff;
    border-radius: 100px;
  }

  .service-info-title {
    font-weight: 700;
    font-size: 32px;
    position: relative;
    bottom: 2px;
    //padding-top: 60px;
  }

  .service-info-subtitle {
    font-size: 16px;
    line-height: 1.5;
    color: #646a73;
    margin-top: 30px;
  }

  .service-list {
    display: flex;
    justify-content: space-evenly;
    text-align: center;
    margin: 70px auto 0 auto;
  }

  .service-title-shadow {
    width: 111px;
    height: 111px;
    border-radius: 50%;
    display: flex;
    justify-content: center;
    align-items: center;
    transition: .3s;
  }

  .service-title-shadow:hover {
    width: 111px;
    height: 111px;
    border-radius: 50%;
    transform: scale(1.05) translateY(-1px);
    box-shadow: 0 6px 20px 0 rgba(0, 0, 0, .15);
  }

  .service-name {
    margin-top: 30px;
    font-weight: 600;
    font-size: 20px;
  }
}

.service-idea {
  background-color: #F5F5F5;
  width: 100%;

  .service-idea {
    max-width: 1440px;
    overflow: hidden;
    display: flex;
  }

  .idea-left img {
    width: 600px;
  }

  .idea-right {
    height: 500px;
    width: calc(100% - 600px);
    margin-left: 100px;
    padding-top: 50px;

    .block-line {
      margin: 0 0 12px 0;
      width: 24px;
      height: 4px;
      background-color: #3370ff;
      border-radius: 100px;
    }

    .idea-title {
      font-weight: 700;
      font-size: 25px;
      position: relative;
      bottom: 10px;
      //padding-top: 60px;
    }

    .idea-subtitle {
      font-size: 16px;
      line-height: 1.5;
      color: #646a73;
      margin-top: 10px;
    }

    img {
      width: 500px;
      height: 200px;
      object-fit: cover;
      margin-top: 40px;
      margin-bottom: 30px;
      padding: 10px;
      border: #d3dce6 2px dashed;
    }

    .idea-desc {
      position: relative;
      bottom: 8px;
      display: -webkit-box;
      -webkit-box-orient: vertical;
      -webkit-line-clamp: 15;
      overflow: hidden;
      max-height: 888px;
      max-width: 888px;
      font-size: 15px;
      line-height: 30px;
      color: #646a73;
      white-space: pre-wrap;
    }

    .el-button {
      margin-top: 40px;
    }
  }
}

.service-case {
  background-color: #FFFFFF;
  width: 100%;

  .service-case {
    max-width: 1440px;
    //height: 700px;
    overflow: hidden;
    margin: 0 auto;
    text-align: center;
    padding-top: 50px;

    .block-line {
      margin: 0 auto 12px;
      width: 24px;
      height: 4px;
      background-color: #3370ff;
      border-radius: 100px;
    }

    .case-title {
      font-weight: 700;
      font-size: 32px;
      position: relative;
      bottom: 2px;
      //padding-top: 60px;
    }

    .case-subtitle {
      font-size: 16px;
      line-height: 1.5;
      color: #646a73;
      margin-top: 10px;
    }

    .case-list {
      display: flex;
      justify-content: space-evenly;
    }

    .el-card {
      width: 247px;
      height: 217px;
      margin-top: 40px;
    }

    .el-progress {
      margin-top: 10px;
    }

    /deep/ .el-progress-bar__outer {
      height: 2px !important;
    }

    .case-desc {
      margin-top: 30px;
      margin-bottom: 60px;
      font-weight: 500;
      font-size: 14px;
    }
  }
}
</style>
