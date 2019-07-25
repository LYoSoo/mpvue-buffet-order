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
      <div class="order-button"><span>自助点单</span></div>
    </div>
    <ul class="limited-time">
      <li>
        <div class="div-inner">
          <div style="flex-grow: 1"><img style="width:60rpx; height: 60rpx;padding-top: 20rpx" src="/static/images/xianshi1.png"></div>
          <span style="flex-grow: 10">限时拼团</span>
          <div style="flex-grow: 1"><img style="width:60rpx; height: 60rpx;padding-top: 20rpx" src="/static/images/xianshi1.png"></div>
        </div>
      </li>
            <li>
        <div class="div-inner">
          <div style="flex-grow: 1"><img style="width:60rpx; height: 60rpx;padding-top: 20rpx" src="/static/images/xianshi1.png"></div>
          <span style="flex-grow: 10">限时拼团</span>
          <div style="flex-grow: 1"><img style="width:60rpx; height: 60rpx;padding-top: 20rpx" src="/static/images/xianshi1.png"></div>
        </div>
      </li>
            <li>
        <div class="div-inner">
          <div style="flex-grow: 1"><img style="width:60rpx; height: 60rpx;padding-top: 20rpx" src="/static/images/xianshi1.png"></div>
          <span style="flex-grow: 10">限时拼团</span>
          <div style="flex-grow: 1"><img style="width:60rpx; height: 60rpx;padding-top: 20rpx" src="/static/images/xianshi1.png"></div>
        </div>
      </li>
    </ul>
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
  methods: {}
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
    line-height: 100rpx;
  }
  .div-inner{
    width: 90%;
    margin: 0 auto;
    display: flex;
    border-bottom: 1px solid #ddd;
  }
</style>
