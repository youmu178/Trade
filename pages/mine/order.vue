<template>
  <view class="content">
    <van-tabs :active="index" sticky animated :border="border" color="#f6411f" titleActiveColor="#f6411f" @change="onChange">
      <van-tab v-for="item in title" :key="item.index" :title="item">
        <view style="margin-top: 15px;" v-for="(it, index) in 5" :key="index">
          <view class="shop-info">
            <view class="shop-view">
              <text class="shop">店铺: XXX</text>
              <text class="order">订单编号：YM24343432434656787</text>
            </view>
            <text class="status">已完成</text>
          </view>
          <view class="item">
            <van-image width="94" height="94" src="https://gw.alicdn.com/bao/uploaded/i1/2206479918978/O1CN018uvMW92GBySgyIic7_!!0-item_pic.jpg_480x480Q75" lazy-load fit="cover" />
            <view class="info">
              <text class="title">爵森马伯特男士春秋装上衣服潮流卫衣秋季男装男装男装</text>
              <text class="sort">XL 黑色</text>
              <view class="money-stepper">
                <text class="money">¥ 99.00</text>
                <text class="number">x 1</text>
              </view>
            </view>
          </view>
          <view class="count-view">
            <text class="title">合计：</text>
            <text class="money">¥99.00</text>
          </view>
          <view class="line"></view>
          <view class="option-view"><van-button plain hairline color="#636465" size="small">查看物流</van-button></view>
        </view>
      </van-tab>
    </van-tabs>
  </view>
</template>

<script>
export default {
  data() {
    return {
      index: 0,
      border: false,
      title: ['全部', '待付款', '已付款', '已发货', '已完成']
    };
  },
  onLoad(option) {
    this.index = parseInt(option.index);
  },
  methods: {
    onChange(evnt) {}
  }
};
</script>
<style>
page {
  background-color: #f5f5f5;
}
</style>
<style scoped lang="scss">
.content {
  padding-bottom: 20px;
  .shop-info {
    display: flex;
    align-items: center;
    padding-left: 15px;
    background: #ffffff;
    height: 60px;
    .shop-view {
      display: flex;
      flex-direction: column;
      .shop {
        color: #555656;
        font-size: 16px;
      }
      .order {
        color: #c0c1c2;
        font-size: 12px;
      }
    }
    .status {
      position: absolute;
      right: 15px;
      transform: translateY(-12px);
      color: #f6411f;
      font-size: 15px;
    }
  }
  .line {
    width: 100%;
    height: 1px;
    background-color: #f5f5f5;
  }
  .item {
    display: flex;
    align-items: center;
    padding: 10px 15px 10px 15px;
    .info {
      display: flex;
      flex-direction: column;
      margin-left: 10px;
      transform: translateY(-3px);
      .title {
        font-size: 14px;
        color: #3b3b3b;
        overflow: hidden;
        text-overflow: ellipsis;
        display: -webkit-box;
        -webkit-line-clamp: 2;
        -webkit-box-orient: vertical;
        word-break: break-all;
      }
      .sort {
        font-size: 12px;
        color: #9c9c9c;
        margin-top: 5px;
      }
      .money-stepper {
        display: flex;
        align-items: center;
        margin-top: 8px;
        .money {
          color: #f6411f;
          font-size: 16px;
        }
        .number {
          position: absolute;
          right: 0px;
          color: #434445;
          font-size: 14px;
        }
      }
    }
  }
  .count-view {
    display: flex;
    justify-content: flex-end;
    align-items: center;
    padding: 10px 15px;
    background: #ffffff;
    .title {
      color: #68696a;
      font-size: 16px;
    }
    .money {
      color: #f6411f;
      font-size: 15px;
    }
  }
  .option-view {
    display: flex;
    justify-content: flex-end;
    padding: 10px 15px;
    background: #ffffff;
  }
}
</style>
