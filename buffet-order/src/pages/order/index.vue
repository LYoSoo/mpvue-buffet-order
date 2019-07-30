<template>
     <div class="main">
       <div class="order-inner">
         <div class="order-div">
           <p>暂无订单信息</p>
         </div>
         <div class="order-button">
           开始点单
         </div>
       </div>
     </div>
</template>

<script>
export default {
}
</script>

<style>
  page{
    background-color: rgb(240,240,240)
  }
  .main{
    width: 100%;
    height: 100%;
    background-color: rgb(240,240,240)
  }
  .order-inner{
    width: 90%;
    margin: 0 auto;
    padding-top: 30rpx;
  }
  .order-div{
    width: 100%;
    height: 300rpx;
    display: flex;
    align-items: center;
    justify-content: center;
    background-color: #FFF;
  }
  .order-div p{
    color: #AAA
  }
  .order-button{
    width: 100%;
    line-height: 100rpx;
    margin-top: 100rpx;
    border-radius: 16rpx;
    background-color: rgb(225,130,50);
    color: #fff;
    text-align: center;
  }
</style>
