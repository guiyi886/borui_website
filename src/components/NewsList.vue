<template>
  <div>
    <ul class="news-list-items" v-if="items !== undefined">
      <li class="news-list-item" v-for="(item, index,) in items" :key="index">
        <el-card shadow="hover">
          <router-link :to="`/news/${item.news_path}`">
            <!--<div class = "item-mask"></div>-->
            <!--<img src="../assets/img/banner1.jpg" alt="">-->
            <img :src="item.cover_img" alt="">
            <!--<img :src="bannerImg" alt="">-->
            <!-- 使用动态绑定 :src -->
            <!--<img :src="getCoverImageUrl(item.cover_img)" alt="">-->
            <!--<img :src="require(`../assets/img/banner1.jpg`)" alt="">-->
            <!--<img :src="require('./assets/'+item.cover_img)" alt="">-->
            <div class="item-content">
              <h2>{{ item.news_title }}</h2>
              <p>{{ item.news_desc }}</p>
              <span>{{ item.publish_time }}</span>
            </div>
          </router-link>
        </el-card>
      </li>
    </ul>
    <span class="is-null" v-else>暂无数据</span>
  </div>
</template>

<script lang="ts" setup>
import { PropType, ref } from 'vue'
import mainStore from '@/store'
// import bannerImg from '@/assets/img/banner1.jpg'

// console.log(bannerImg)
const props = defineProps({
  items: {
    type: Array as PropType<Array<any>>,
    default: () => ([])
  }
})

const currentPage = ref(1)

function setArticlePath (path: string) {
  // console.log("path====>",path);
  mainStore.commit('SET_ARTICLE_PATH', {
    path: path
  })
}

// function getCoverImageUrl(coverImg: string): string {
//   // 使用 require 动态加载图片路径
//   return new URL(`../assets/icon/${coverImg}`, import.meta.url).href
// }
</script>

<style lang="less" scoped>
.news-list-item {
  padding: 0 15px 15px 8px;
  position: relative;
  border-radius: 8px;

  img {
    width: 366px;
    height: 298px;
    border-style: none;
    //浅蓝色边框
    border: 3px solid #8dc5ff; /* 使用浅蓝色作为边框颜色 */
    border-radius: 28px; /* 圆角 */
    padding: 10px; /* 内边距 */
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.2); /* 阴影效果 */
  }

  a {
    color: rgba(0, 0, 0, 1);
    transition: color .3s;
    overflow: hidden;
    display: flex;
    cursor: pointer;
  }

  a:hover {
    color: var(--hover_color);
  }
}

.el-card {
  border: none;
  transition: .5s;
}

.is-null {
  display: flex;
  justify-content: center;
  margin-top: 45px;
  color: #777
}

.item-mask {
  display: block;
  position: absolute;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0);
  transition: all .3s;
  border-radius: 8px;
}

.item-content {
  margin-left: 40px;
  width: calc(100% - 238px);
  //浅蓝色边框
  border: 3px solid #8dc5ff; /* 使用浅蓝色作为边框颜色 */
  border-radius: 28px; /* 圆角 */
  padding: 10px; /* 内边距 */
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.2); /* 阴影效果 */

  h2 {
    //上边距
    margin-top: 111px;
    margin-left: 15px;
    color: rgba(0, 0, 0, .7);
    font-size: 28px;
    font-weight: 500;
    overflow: hidden;
    //white-space: nowrap;
    text-overflow: ellipsis;
    display: -webkit-box;
    -webkit-box-orient: vertical;
    -webkit-line-clamp: 2;
  }

  p {
    margin: 10px 0;
    font-size: 15px;
    color: #777;
    letter-spacing: 0;
    line-height: 22px;
    overflow: hidden;
    //white-space: nowrap;
    text-overflow: ellipsis;
    display: -webkit-box;
    -webkit-box-orient: vertical;
    -webkit-line-clamp: 1;
  }

  span {
    color: #b8b8b8;
    line-height: 14px;
  }
}
</style>
