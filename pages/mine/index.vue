<template>
  <view class="content">
    <view class="head">
      <van-image width="50" height="50" fit="cover" round src="https://img.yzcdn.cn/vant/cat.jpeg" />
      <text class="name">XXXX</text>
    </view>
    <view class="card">
      <view class="order-title-view">
        <text class="order-title">我的订单</text>
        <view class="order-title-all">
          <text class="order-all">查看全部订单</text>
          <van-icon name="arrow" color="#838383" />
        </view>
      </view>
      <view class="line"></view>
      <view class="order-status">
        <view class="order-item">
          <van-icon name="pending-payment" size="30" color="#4c4c4c" />
          <text>待付款</text>
        </view>
        <view class="order-item">
          <van-icon name="paid" size="30" color="#4c4c4c" />
          <text>已付款</text>
        </view>
        <view class="order-item">
          <van-icon name="logistics" size="30" color="#4c4c4c" />
          <text>已发货</text>
        </view>
        <view class="order-item">
          <van-icon name="sign" size="30" color="#4c4c4c" />
          <text>已完成</text>
        </view>
      </view>
    </view>
    <view class="card">
      <van-cell title="我的地址" icon="location-o" is-link clickable/>
      <van-cell title="我的积分" icon="medal-o" is-link clickable/>
      <van-cell title="关于我们" icon="friends-o" is-link clickable/>
    </view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      title: 'Hello'
    };
  },
  onLoad() {},
  methods: {}
};
</script>
<style>
page {
  background-color: #f5f5f5;
}
</style>
<style scoped lang="scss">
.content {
  .head {
    display: flex;
    align-items: center;
    height: 120px;
    background: linear-gradient(180deg, rgba(250, 182, 73, 1) 30%, rgba(246, 133, 89, 1) 100%);
    van-image {
      margin-left: 20px;
    }
    .name {
      margin-left: 10px;
      color: #232323;
      font-size: 15px;
    }
  }
  .line {
    width: 100%;
    height: 1px;
    background-color: #f5f5f5;
    margin-left: 15px;
  }
  .card {
    background-color: #ffffff;
    margin: 15px;
    border-radius: 5px;
    overflow: hidden;
  }
  .order-title-view {
    display: flex;
    align-items: center;
    height: 45px;
    padding-left: 15px;
    .order-title {
      color: #232323;
      font-size: 15px;
      font-weight: 500;
    }
    .order-title-all {
      color: #737373;
      display: flex;
      align-items: center;
      position: absolute;
      right: 30px;
      text {
        color: #737373;
        font-size: 14px;
      }
    }
  }
  .order-status {
    display: flex;
    justify-content: space-around;
    margin-top: 20px;
    padding-bottom: 20px;
    .order-item {
      display: flex;
      flex-direction: column;
      text {
        color: #4c4c4c;
        font-size: 12px;
        margin-top: 5px;
      }
    }
  }
}
</style>
