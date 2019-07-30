<template>
  <div class="inner-div">
    <div class="avtor">
      <img v-if="!isShow" class="img-item" src="/static/images/user.png" />
      <img v-if="isShow" class="img-item" :src="userInfo.avatarUrl">
    </div>
    <p class="name">{{userInfo.nickName || '欢迎您'}}</p>
    <button class="login" v-if="!isShow" open-type='getUserInfo' @getuserinfo="bindGetUserInfo">您好，请先登陆</button>
    <ul class="userInfo">
      <li>
        <div class="div-inner">
          <div>
            <img class="img-items" src="/static/images/xianshi.png" />
          </div>
          <span>限时拼团</span>
          <div>
            <img class="img-right" src="/static/images/right.png" />
          </div>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data () {
    return {
      isShow: false,
      userInfo: ''
    }
  },
  onShow () {
    this.getInfo()
    wx.showLoading({
      title: '加载中...'
    })
  },
  methods: {
    bindGetUserInfo (e) {
      if (e.mp.detail.userInfo) {
        console.log('用户点击了授权')
        this.getInfo()
      } else {
        console.log('取消授权')
      }
    },
    getInfo () {
      // 获取授权
      wx.getSetting({
        success: res => {
          wx.hideLoading()
          if (res.authSetting['scope.userInfo']) {
            this.isShow = true
            wx.getUserInfo({
              success: data => {
                console.log(data)
                this.userInfo = data.userInfo
              },
              faild: () => {
                console.log('失败')
              }
            })
          } else {
            this.isShow = false
          }
        }
      })
    }
  }
}
</script>

<style>
page {
  background-color: rgb(240, 240, 240);
}
.inner-div {
  width: 90%;
  margin: 0 auto;
}
.avtor {
  width: 100%;
  height: 300rpx;
  display: flex;
  justify-content: center;
  align-items: center;
}
.img-item {
  display: flex;
  width: 250rpx;
  height: 250rpx;
  border-radius: 250rpx;
}
.name {
  text-align: center;
}
.userInfo {
  background-color: rgba(254, 254, 254);
  margin-top: 60rpx;
}
.userInfo li {
  width: 100%;
  line-height: 100rpx;
  border-bottom: 1rpx solid #eee;
}
.div-inner {
  display: flex;
}
.img-items {
  width: 60rpx;
  height: 60rpx;
  padding-top: 20rpx;
  padding-left: 20rpx;
}
.div-inner span {
  flex-grow: 10;
}
.div-inner div {
  flex-grow: 1;
}
.img-right {
  width: 30rpx;
  height: 30rpx;
}
.login{
    background-color: rgb(75,192,103);
    color: #fff
}
</style>
