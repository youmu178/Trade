<template>
  <view>
    <view v-show="isEmptyAddress" class="empty-address" @click="onEmptyAddressClick"><text>请添加您的收货地址</text></view>
    <view style="height: 10px; width: 100%; background-color: #f5f5f5;"></view>
    <view class="goods">
      <view class="item-goods">
        <van-image class="img" width="65" height="65" lazy-load fit="cover" :src="goods.img" />
        <view class="item-goods-info">
          <text class="title">{{ goods.title }}</text>
          <text class="cc">{{ goods.chicun + '/' + goods.color }}</text>
        </view>
        <text class="zhekoujia">¥{{ goods.money }}</text>
        <text class="number">{{ 'x' + goods.goodsNumber }}</text>
      </view>
    </view>
    <view class="goods-list">
      <text class="sub-title">快递费</text>
      <text class="sub-title-r">0.00</text>
    </view>
    <view class="line"></view>
    <view class="goods-list">
      <text class="sub-title">备注</text>
      <input style="color: #666666;" />
    </view>
    <view style="position: absolute; right: 20px; margin-top: 30px; margin-bottom: 52px;">
      <text style="color: #3b3b3b; font-size: 12px;">共X件商品 合计¥</text>
      <text style="color: #f50000; font-size: 18px; font-weight: 500;">99.00</text>
    </view>
    <van-submit-bar :loading="submitLoading" :price="money" button-text="提交订单" @submit="onSubmit" />
  </view>
</template>

<script>
export default {
  data() {
    return {
      isEmptyAddress: true,
      submitLoading: false,
      money: 3050,
      goods: {}
    };
  },
  onLoad(option) {
    const goods = JSON.parse(decodeURIComponent(option.detail));
    console.log(goods);
    this.goods = goods;
  },
  methods: {
    onSubmit() {
      this.submitLoading = true;
      setTimeout(() => {
        this.submitLoading = false;
      }, 1000);
    },
    onEmptyAddressClick() {
      uni.navigateTo({
        url: '/pages/mine/address-add'
      });
    }
  }
};
</script>
<style>
page {
  background-color: #FFFFFF;
}
</style>
<style scoped lang="scss">
.empty-address {
  height: 100px;
  text-align: center;
  text {
    font-size: 16px;
    color: #9c9c9c;
    line-height: 100px;
  }
}
.line {
  width: 100%;
  height: 1px;
  background-color: #f5f5f5;
}
.goods {
  background-color: #f5f5f5;
  margin: 12px 10px 10px 10px;
  border-radius: 3px;
  .item-goods {
    display: flex;
    .img {
      margin: 8px 5px;
    }
    .item-goods-info {
      flex-direction: column;
      margin-top: 8px;
      margin-left: 3px;
      .title {
        color: #3b3b3b;
        font-size: 13px;
        margin-right: 75px;
        margin-bottom: 5px;
        overflow: hidden;
        text-overflow: ellipsis;
        display: -webkit-box;
        -webkit-line-clamp: 2;
        -webkit-box-orient: vertical;
        word-break: break-all;
      }
      .cc {
        background-color: #d0d0d0;
        color: #6c6c6c;
        font-size: 12px;
        border-radius: 10px;
        padding-left: 10px;
        padding-right: 10px;
        height: 30px;
        line-height: 30px;
      }
    }
    .zhekoujia {
      color: #f50000;
      font-weight: 500;
      font-size: 14px;
      position: absolute;
      right: 16px;
      margin-top: 10px;
    }
    .number {
      position: absolute;
      right: 16px;
      margin-top: 50px;
    }
  }
}
.goods-list {
  display: flex;
  align-items: center;
  height: 40px;
  margin-left: 15px;
  margin-right: 15px;
  .sub-title {
    color: #3b3b3b;
    font-size: 13px;
    margin-right: 10px;
  }
  .sub-title-r {
    color: #494949;
    font-size: 13px;
    position: absolute;
    right: 16px;
  }
}
</style>
