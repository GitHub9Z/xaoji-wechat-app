<template>
  <div class="content">
    <ul class="article-list">
      <li class="article-list-item" v-for="tab in tabs" :key="tab">
        <img class="article-img" :src="articleimgsrc" />
        <div>
          <div>文章标题</div>
          <div class="article-intro">文章摘要文章摘要文章摘要文章摘要文章摘要</div>
          <div class="icon-tab">
            <img class="icon" :src="imgsrc">
            <div class="text">18920</div>
            <img class="icon" :src="imgsrc">
            <div class="text">13320</div>
          </div>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        articleimgsrc: "/static/images/img_article.jpeg",
        imgsrc: "/static/images/icon_zan_up.png",
        tabs: [{
            text: '巴士'
          },
          {
            text: '快车'
          },
          {
            text: '专车'
          },
          {
            text: '顺风车'
          },
          {
            text: '出租车'
          },
          {
            text: '代驾'
          }
        ],
      }
    },
    methods: {}
  }

</script>

<style>
  .article-list {
    width: 100%;
  }

  .article-list-item {
    height: 100px;
    width: 100%;
    display: flex;
    margin-top: 1px;
    flex-direction: row;
    align-items: center;
    background: rgb(255, 255, 255);
  }

  .article-img {
    width: 120px;
    height: 80px;
    margin-left: 10px;
    margin-right: 10px;
  }

  .icon {
    width: 20px;
    height: 10px;
    margin-left: 10px;
    margin-right: 10px;
  }

  .text {
    font-size: 12px;
    color: rgb(99, 99, 99)
  }

  .icon-tab {
    display: flex;
    flex-direction: row;
    align-items: center;
  }

  .article-intro {
    font-size: 14px;
    color: rgb(99, 99, 99)
  }

</style>
