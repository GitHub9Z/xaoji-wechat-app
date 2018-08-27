<template>
  <div class="container">
    <i-tabs :current="current_scroll">
      <i-tab key="tab1" title="选项1" @click="handleChangeScroll('tab1')"></i-tab>
      <i-tab key="tab2" title="选项2" @click="handleChangeScroll('tab2')"></i-tab>
      <i-tab key="tab3" title="选项3" @click="handleChangeScroll('tab3')"></i-tab>
      <i-tab key="tab4" title="选项4" @click="handleChangeScroll('tab4')"></i-tab>
      <i-tab key="tab5" title="选项5" @click="handleChangeScroll('tab5')"></i-tab>
      <i-tab key="tab6" title="选项6" @click="handleChangeScroll('tab6')"></i-tab>
      <i-tab key="tab7" title="选项7" @click="handleChangeScroll('tab7')"></i-tab>
      <i-tab key="tab8" title="选项8" @click="handleChangeScroll('tab8')"></i-tab>
      <i-tab key="tab9" title="选项9" @click="handleChangeScroll('tab9')"></i-tab>
    </i-tabs>
    <div class="userinfo" @click="bindViewTap">
      <img class="userinfo-avatar" v-if="userInfo.avatarUrl" :src="userInfo.avatarUrl" background-size="cover" />
      <div class="userinfo-nickname">
        <card :text="userInfo.nickName"></card>
      </div>
      <img class="userinfo-more" src="/static/images/icon_more.png" />
    </div>

    <div class="userdata">
      <div class="userdata-attention">
        <div>关注</div>
        <div class="userdata-attention-num">20</div>
      </div>
      <div class="userdata-attention">
        <div>文章</div>
        <div class="userdata-attention-num">132</div>
      </div>
      <div class="userdata-attention">
        <div>点赞</div>
        <div class="userdata-attention-num">2.3w</div>
      </div>
    </div>
    <ul class="info-list">
      <li class="info-list-item" @click="clickHandle('to card', $event)" v-for="tab in tabs" :key="tab">
        <img class="item-icon" src="/static/images/icon_btn.png" />
        <div>我的文章</div>
      </li>
    </ul>
    <div class="usermotto">
      <div class="user-motto">
        <card :text="motto"></card>
      </div>
    </div>

    <form class="form-container">
      <input type="text" class="form-control" v-model="motto" placeholder="v-model" />
      <input type="text" class="form-control" v-model.lazy="motto" placeholder="v-model.lazy" />
    </form>
    <a href="/pages/counter/main" class="counter">去往Vuex示例页面</a>
    <!--<div>
      <m-tabbar v-model="select">
        <m-tabbar-item id='tab1'>
          <img src="/static/images/icon_tab_user_up.png" alt="" slot="icon-normal">
          <img src="/static/images/icon_tab_user_down.png" alt="" slot="icon-active"> 首页
        </m-tabbar-item>
        <m-tabbar-item id='tab2'>
          <img src="/static/images/icon_tab_user_up.png" alt="" slot="icon-normal">
          <img src="/static/images/icon_tab_user_down.png" alt="" slot="icon-active"> 书影音
        </m-tabbar-item>
        <m-tabbar-item id='tab3'>
          <img src="/static/images/icon_tab_user_up.png" alt="" slot="icon-normal">
          <img src="/static/images/icon_tab_user_down.png" alt="" slot="icon-active"> 广播
        </m-tabbar-item>
        <m-tabbar-item id='tab4'>
          <img src="/static/images/icon_tab_user_up.png" alt="" slot="icon-normal">
          <img src="/static/images/icon_tab_user_down.png" alt="" slot="icon-active"> 小组
        </m-tabbar-item>
        <m-tabbar-item id='tab5'>
          <img src="/static/images/icon_tab_user_up.png" alt="" slot="icon-normal">
          <img src="/static/images/icon_tab_user_down.png" alt="" slot="icon-active"> 我的
        </m-tabbar-item>
      </m-tabbar>
    </div>-->
  </div>
</template>

<script>
  import card from '../../components/card'
  //import mTabbar from '../../components/tabbar'
  //import mTabbarItem from '../../components/tabbar-item'
  export default {
    name: 'index',
    data() {
      return {
        current_scroll: 'tab1',
        motto: 'Hello World',
        userInfo: {},
        select: "tab1",
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
    components: {
      card,
      //mTabbar,
      //mTabbarItem
    },

    methods: {
      bindViewTap() {
        const url = '../logs/main'
        wx.navigateTo({
          url
        })
      },
      getUserInfo() {
        // 调用登录接口
        wx.login({
          success: () => {
            wx.getUserInfo({
              success: (res) => {
                this.userInfo = res.userInfo
              }
            })
          }
        })
      },
      clickHandle(msg, ev) {
        if (msg == "to card") {
          var url = "../counter/main";
          wx.navigateTo({
            url
          });
          console.log('clickHandle:', msg, ev)
        }
      },
      cardpage() {
        var url = "../counter/main";
        wx.navigateTo({
          url
        });
      },
      handleChangeScroll(key) {
          this.current_scroll = key;
      }
    },

    created() {
      // 调用应用实例的方法获取全局数据
      this.getUserInfo()
    },
  }

</script>
<style scoped>
  .userinfo {
    margin: 0;
    height: 170rpx;
    width: 100%;
    display: flex;
    flex-direction: row;
    align-items: center;
    background: rgb(255, 255, 255);
  }

  .userinfo-avatar {
    width: 128rpx;
    height: 128rpx;
    margin: 40rpx;
    border-radius: 50%;
  }

  .userinfo-nickname {
    color: #aaa;
  }

  .userinfo-more {
    width: 30px;
    height: 30px;
    margin-left: 135px;
  }

  .userdata {
    margin-top: 1px;
    height: 170rpx;
    width: 100%;
    display: flex;
    flex-direction: row;
    align-items: center;
    background: rgb(255, 255, 255);
    margin-bottom: 15rpx;
  }

  .userdata-attention {
    width: 33.4%;
    text-align: center;
  }

  .info-list {
    width: 100%;
  }

  .info-list-item {
    height: 50px;
    width: 100%;
    display: flex;
    margin-top: 1px;
    flex-direction: row;
    align-items: center;
    background: rgb(255, 255, 255);
  }

  .item-icon {
    width: 30px;
    height: 30px;
    margin-left: 20px;
    margin-right: 10px;
  }

  .usermotto {
    margin-top: 100px;
  }

  .form-control {
    display: block;
    padding: 0 12px;
    margin-bottom: 5px;
    border: 1px solid #ccc;
  }

  .counter {
    display: inline-block;
    margin: 10px auto;
    padding: 5px 10px;
    color: blue;
    border: 1px solid blue;
  }

</style>
