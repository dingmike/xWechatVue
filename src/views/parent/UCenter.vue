<template>
  <div class="study-page">
    <div class="cl-module">
      <div class="cl-m-body">
        <div>
          <img :src="user.wechat_user.avatar">
        </div>
        <div>
          <p>
            {{user.wechat_user.nickname}}
          </p>
          <p>
            {{user.id}}
          </p>
        </div>
      </div>
      <div class="arrows">
        <span slot="icon" class="iconfont icon-right"></span>
      </div>
    </div>
    <div class="cl-module">
          <cell title="我的成长" :value="user.parent.month_experience" link="/parent/user/grow" is-link></cell>
          <cell title="我的积分" :value="user.parent.credit" link="/parent/coupon/convert" is-link></cell>
          <cell title="我的卡券" link="/parent/coupon/my_coupon" :value="user.parent.coupon" is-link></cell>
          <cell title="我的共读" link="/parent/course/reader_favorite" is-link></cell>
          <cell title="我的共学" link="/parent/course/my_learn/1" is-link></cell>
          <cell title="我的共玩" link="/parent/course/manage" is-link></cell>
      </div>
      <tabbar>
        <tabbar-item link="/parent/home" >
          <span slot="icon" class="iconfont icon-home"></span>
          <span slot="label">主页</span>
        </tabbar-item>
        <tabbar-item link="/parent/ucenter" selected>
          <span slot="icon" class="iconfont icon-ucenter"></span>
          <span slot="label">个人</span>
        </tabbar-item>
      </tabbar>
  </div>
</template>

<script>
import {
  Tabbar,
  Cell,
  Group,
  Badge,
  TabbarItem
} from 'vux'
import userModule from 'lanmaLib/modules/user'

export default {
  components: {
    Tabbar,
    TabbarItem,
    Cell,
    Group,
    Badge
  },
  data () {
    return {
      user: {
        wechat_user: {},
        parent: {}
      }
    }
  },
  created () {
    userModule.getCurrentUserInfo().then((userInfo) => {
      console.log(userInfo)
      this.user = userInfo
    })
  },
  methods: {
    click () {
      console.log('点击了')
    }
  }
}
</script>

<style scoped lang="scss">
.cl-m-body{
  padding-top: 5px;
  div{
    float: left;
  }
  div:nth-child(even){
    margin-left: 15px;
    margin-top: 10px;
  }
  img{
    border: 0.5px solid #b4b4b4;
    border-radius: 4.5px;
    width: 64px;
    height: 64px;
  }
  p:nth-child(even){
    color:#9b9b9b;
  }
}
.arrows{
  opacity:0.5;
  float: right;
  margin-right: 10px;
  margin-top: 5px;
}
</style>
