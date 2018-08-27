<template>
  <div class="content">
    <div class="B">
      <ul>
        <li class='li1' @click="listclick">
          <a class='top-a' id='current-item'>综合排序
            <img class="icon-arrow" :src="arrow" />
          </a>
          <div class="C D">
            <a class='top-a' :style='{display: liststate}'>时间排序</a>
            <a class='top-a' :style='{display: liststate}'>热度排序</a>
          </div>
        </li>
        <li class='li1' @click="secondlistclick">
          <a class='top-a' id='current-item'>全部标签
            <img class="icon-arrow" :src="secondarrow" />
          </a>
          <div class="C D">
            <a class='top-a' :style='{display: secondliststate}'>周边配套</a>
            <a class='top-a' :style='{display: secondliststate}'>硬件设施</a>
            <a class='top-a' :style='{display: secondliststate}'>特殊情况</a>
          </div>
        </li>
      </ul>
    </div>
    <div class="E">
      <ul class="info-list">
        <li class="info-list-item" v-for="tab in tabs" :key="tab">
          <img class="item-icon" src="/static/images/icon_user.png" />
          <div>
            <div>用户名称</div>
            <div class="user-intro">用户简介用户简介用户简介用户简介</div>
          </div>
          <a class="zan" v-on:click="change">
            <img class="zan-icon" :src="imgsrc">
          </a>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
  // Use Vuex
  import store from './store'

  export default {
    data() {
      return {
        liststate: 'none',
        secondliststate: 'none',
        arrow: "/static/images/icon_arrow_down.png",
        secondarrow: "/static/images/icon_arrow_down.png",
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
    computed: {
      count() {
        return store.state.count
      }
    },
    methods: {
      increment() {
        store.commit('increment')
      },
      decrement() {
        store.commit('decrement')
      },
      change() {
        if (this.imgsrc == '/static/images/icon_zan_up.png') {
          this.imgsrc = '/static/images/icon_zan_down.png';
        } else {
          this.imgsrc = '/static/images/icon_zan_up.png';
        }
      },
      listclick() {
        if (this.liststate == 'block') {
          this.liststate = 'none';
          this.arrow = "/static/images/icon_arrow_down.png";
          console.log('关闭');
        } else {
          this.liststate = 'block';
          this.secondliststate = 'none';
          this.arrow = "/static/images/icon_arrow_up.png";
          console.log('打开');
        }
      },
      secondlistclick() {
        if (this.secondliststate == 'block') {
          this.secondliststate = 'none';
          this.secondarrow = "/static/images/icon_arrow_down.png";
          console.log('关闭');
        } else {
          this.secondliststate = 'block';
          this.liststate = 'none';
          this.secondarrow = "/static/images/icon_arrow_down.png";
          console.log('打开');
        }
      }
    }
  }

</script>

<style>
  .E {
    z-index: 1;
  }

  .info-list {
    width: 100%;
    padding: 48px 0 0 0;
  }

  .info-list-item {
    height: 100px;
    width: 100%;
    display: flex;
    margin-top: 1px;
    flex-direction: row;
    align-items: center;
    font-size: 15px;
    font-weight: bold;
    background: rgb(255, 255, 255);
  }

  .item-icon {
    width: 50px;
    height: 50px;
    margin-left: 20px;
    margin-right: 10px;
  }

  .zan-icon {
    width: 30px;
    height: 30px;
    margin-left: 20px;
    margin-right: 10px;
  }

  .icon-arrow {
    width: 15px;
    height: 15px;
    margin-left: 5px;
    margin-right: 10px;
  }

  * {
    padding: 0;
    margin: 0;
  }

  .li1 {
    width: 50%;
    height: 30px;
    background: rgb(250, 250, 250);
    text-align: center;
  }

  .top-a {
    text-decoration: none;
    background: rgb(250, 250, 250);
    text-align: center;
    padding: 8px 0;
  }

  a {
    color: #cdcdcd;
    font-weight: bold;
    font-size: 15px;
  }

  .B {
    z-index: 999;
    width: 100%;
    position: absolute;
  }

  .B li {
    float: left;
  }

  .C {
    clear: both;
  }

  .C a {
    display: none;
  }

</style>
