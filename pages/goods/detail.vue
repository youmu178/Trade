<template>
  <view class="body">
    <swiper class="swiper" circular>
      <swiper-item v-for="item in img" :key="item.index"><image :src="item" lazy-load mode="aspectFill" class="swiper-image"></image></swiper-item>
    </swiper>
    <view class="jia">
      <text class="zhekoujia">¥ 99.00</text>
      <text class="yuanjia">¥ 999.00</text>
    </view>
    <view class="title-view"><text class="title">爵森马伯特男士春秋装上衣服潮流卫衣秋季男装2019新款潮爵森马伯特男士春秋装上衣服潮流卫衣秋季男装</text></view>
    <view class="line"></view>
    <text class="sub-title">尺寸</text>
    <view class="chicun-view">
      <text v-for="(item, index) in chicunList" :key="item.id" class="chicun" :class="{ chicunsel: index == ccSelIndex }" @click="onChicunClick(index)">{{ item }}</text>
    </view>
    <view class="line"></view>
    <text class="sub-title">颜色分类</text>
    <view class="color-view">
      <text v-for="(item, index) in colorList" :key="item.id" class="color" :class="{ colorsel: index == colorSelIndex }" @click="onColorClick(index)">{{ item }}</text>
    </view>
    <view class="line"></view>
    <view class="buy-number-view">
      <text class="sub-title">购买数量</text>
      <van-stepper value="1" min="1" max="10" @change="onChangeNumber" class="number-stepper" />
    </view>
    <view class="line"></view>
    <van-goods-action safe-area-inset-bottom class="goods-action">
      <van-goods-action-icon class="cart-action" icon="cart-o" text="购物车" :info="cartNumber" @click="onClickCart" />
      <van-goods-action-button text="加入购物车" type="warning" @click="onClickAddCart" />
      <van-goods-action-button text="立即购买" @click="onClickBuy" />
    </van-goods-action>
  </view>
</template>

<script>
export default {
  data() {
    return {
      swiperData: [],
      ccSelIndex: 0,
      ccSelText: '',
      colorSelIndex: 0,
      colorSelText: '',
      cartNumber: 0,
      goodsNumber: 1,
      img: [
        'https://gw.alicdn.com/bao/uploaded/i1/2206479918978/O1CN018uvMW92GBySgyIic7_!!0-item_pic.jpg_480x480Q75',
        'https://gw.alicdn.com/bao/uploaded/i2/2206479918978/O1CN01N00v3R2GByRYeCD1v_!!0-item_pic.jpg_480x480Q75',
        'https://gw.alicdn.com/bao/uploaded/i1/3816165381/O1CN01Q4PHtO1pcXoQw3olL_!!0-item_pic.jpg_480x480Q75',
        'https://gw.alicdn.com/bao/uploaded/i4/3516851626/O1CN01ur82BD1NskYinadJE_!!0-item_pic.jpg_480x480Q75',
        'https://gw.alicdn.com/bao/uploaded/i3/3524443782/O1CN01bjNnGk1doCU6iys5B_!!0-item_pic.jpg_480x480Q75',
        'https://gw.alicdn.com/bao/uploaded/i1/2206617745862/O1CN01u1SACe1tAqK4BguQS_!!0-item_pic.jpg_480x480Q75',
        'https://gw.alicdn.com/bao/uploaded/i4/2201717159611/O1CN01c8hOq92Krt9eLzFVx_!!0-item_pic.jpg_480x480Q75'
      ],
      chicunList: ['S', 'M', 'L', 'XL', 'XXL', 'XXXL'],
      colorList: ['白色', '红色', '粉色', '黑色']
    };
  },
  onLoad(option) {
    console.log(option);
  },
  methods: {
    onChicunClick(index) {
      this.ccSelIndex = index;
      this.ccSelText = this.chicunList[index];
    },
    onColorClick(index) {
      this.colorSelIndex = index;
      this.colorSelText = this.colorList[index];
    },
    onChangeNumber(event) {
      this.goodsNumber = event.detail;
    },
    onClickCart() {
      uni.switchTab({
        url: '/pages/cart/index'
      })
    },
    onClickAddCart() {
      this.cartNumber++;
    },
    onClickBuy() {
      let goods = {
        img: 'https://gw.alicdn.com/bao/uploaded/i1/2206479918978/O1CN018uvMW92GBySgyIic7_!!0-item_pic.jpg_480x480Q75',
        chicun: this.ccSelText,
        color: this.colorSelText,
        goodsNumber: this.goodsNumber,
        money: '99.00',
        title: '爵森马伯特男士春秋装上衣服潮流卫衣秋季男装2019新款潮爵森马伯特男士春秋装上衣服潮流卫衣秋季男装'
      };
      uni.navigateTo({
        url: '/pages/goods/buy' + '?detail=' + encodeURIComponent(JSON.stringify(goods))
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
.goods-action {
  & ::v-deep {
    .van-button {
      padding-left: 15px;
      margin-right: 30px;
    }
  }
  // .cart-action {
  //   .van-goods-action-icon {
  //     width: 90px !important;
  //   }
  // }
}
.swiper {
  width: 100%;
  height: 320px;
  .swiper-image {
    width: 100%;
    height: 100%;
  }
}
.jia {
  display: flex;
  align-items: center;
  margin: 8px 2px 0px 10px;
  .zhekoujia {
    color: #f50000;
    font-weight: 500;
    font-size: 18px;
  }
  .yuanjia {
    font-size: 12px;
    color: #9c9c9c;
    margin-left: 2px;
    text-decoration: line-through;
  }
}
.title-view {
  padding: 2px 10px;
  .title {
    color: #3b3b3b;
    font-size: 14px;
    font-weight: 450;
  }
}
.sub-title {
  color: #3b3b3b;
  font-size: 12px;
  margin-left: 10px;
}
.line {
  width: 100%;
  height: 1px;
  background-color: #f5f5f5;
  margin: 10px;
}
.buy-number-view {
  display: flex;
  align-items: center;
  padding-top: 5px;
  padding-bottom: 5px;
  .number-stepper {
    position: absolute;
    right: 10px;
  }
}
.chicun-view {
  display: flex;
  flex-wrap: wrap;
  margin-top: 5px;
  margin-bottom: 5px;
  .chicun {
    margin-left: 10px;
    margin-top: 8px;
    background: #f6f7f9;
    border-radius: 2px;
    height: 28px;
    padding: 0 10px;
    line-height: 28px;
    color: #242629;
    font-size: 13px;
  }
  .chicunsel {
    background: #f6411f;
    border-radius: 2px;
    color: #ffffff;
  }
}
.color-view {
  display: flex;
  flex-wrap: wrap;
  margin-top: 5px;
  margin-bottom: 5px;
  .color {
    margin-left: 10px;
    margin-top: 8px;
    background: #f6f7f9;
    border-radius: 2px;
    height: 28px;
    padding: 0 10px;
    line-height: 28px;
    color: #242629;
    font-size: 13px;
  }
  .colorsel {
    background: #f6411f;
    border-radius: 2px;
    color: #ffffff;
  }
}
</style>
