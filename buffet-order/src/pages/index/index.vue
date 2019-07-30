<template>
  <div>
    <swiper
      circular=true
      indicator-dots=false
      autoplay=true
      interval=3500
      duration=700
      class="swiper-o"
    >
      <block v-for="item in imgUrls" :key="item">
        <swiper-item class="swiper-item">
          <image :src="item" class="slide-image" />
        </swiper-item>
      </block>
    </swiper>
    <div class="order-div">
      <button class="order-button" v-if="!isShow" open-type='getUserInfo' @getuserinfo="bindGetUserInfo"><span>自助点单</span></button>
    </div>
    <ul class="limited-time">
      <li>
        <div class="div-inner">
          <div><img class="img-item" src="/static/images/xianshi.png"></div>
          <span>限时拼团</span>
          <div><img class="img-item img-right" src="/static/images/right.png"></div>
        </div>
      </li>
      <li>
        <div class="div-inner">
          <div><img class="img-item" src="/static/images/movie.png"></div>
          <span>都可影院</span>
          <div><img class="img-item img-right" src="/static/images/right.png"></div>
        </div>
      </li>
      <li>
        <div class="div-inner">
          <div ><img class="img-item" src="/static/images/money.png"></div>
          <span>CoCo钱包</span>
          <div ><img class="img-item img-right" src="/static/images/right.png"></div>
        </div>
      </li>
    </ul>
    <div class="buttom-img">
      <img src="/static/images/bottom-img.png">
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      imgUrls: [
        'https://i.loli.net/2019/07/25/5d3974a7cde5555223.jpg',
        'https://i.loli.net/2019/07/25/5d3974a7ebe4711659.jpg',
        'https://i.loli.net/2019/07/25/5d3974a811cde37488.jpg'
      ],
      indicatorDots: false,
      autoplay: true,
      interval: 5000,
      duration: 1000
    }
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
                wx.navigateTo({
                  url: '/pages/location/location'
                })
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

<style scoped>
  .swiper-o{
    height: 350rpx;
    width: 100%;
  }
  .swiper-item{
    width: 100%;
    height: 350rpx;
  }
  .slide-image{
    width: 100%;
    height: 100%;
  }
  .order-div{
    width: 100%;
    height: 160rpx;
    background-color: #fff;
    display: flex;
    flex-direction: column;
    justify-content: center
  }
  .order-button{
    width: 60%;
    line-height: 80rpx;
    border: 1px solid rgb(225,130,50);
    display: flex;
    margin: 0 auto;   
    border-radius: 20rpx;
  }
  .order-button span{
    display: block;
    width: 100%;
    text-align: center;
    color: rgb(225,130,50)
  }
  .limited-time{
    width: 100%;
    height: 300rpx;
  }
  .limited-time li{
    width: 100%;
    height: 100rpx;
    line-height: 100rpx;
  }
  .div-inner{
    width: 90%;
    height: 100rpx;
    margin: 0 auto;
    display: flex;
    border-bottom: 1px solid #ddd;
  }
  .div-inner div{
    flex-grow: 1;
  }
  .div-inner span{
    flex-grow: 10;
  }
  .img-item{
    width:60rpx;
    height: 60rpx;
    padding-top: 20rpx;
  }
  .buttom-img{
    width: 100%;
    height: 300rpx;
  }
  .buttom-img img{
    width: 100%;
    height: 100%;
  }
  .img-right{
    width: 30rpx;
    height: 30rpx;
  }
</style>
