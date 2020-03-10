<template>
  <view>
    <swiper class="swiper" circular :indicator-color="indicatorColor" :indicator-active-color="indicatorActiveColor">
        <swiper-item v-for="item in img" :key="item.index"><image :src="item" lazy-load mode="aspectFill" class="swiper-image"></image></swiper-item>
      </swiper>
      <!-- <view class="cart">
        <van-icon name="shopping-cart-o" color="white" size="30px" info="9" />
        <text class="add">加入购物车</text>
      </view> -->
      <van-goods-action>
        <van-goods-action-icon icon="cart-o" text="购物车" bind:click="onClickIcon" />
        <van-goods-action-button text="加入购物车" type="warning" bind:click="onClickButton" />
        <van-goods-action-button text="立即购买" bind:click="onClickButton" />
      </van-goods-action>
    </view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      swiperData: [],
      indicatorColor: '#FFFFFF',
      indicatorActiveColor: '#F6411F',
      img: [
        'https://gw.alicdn.com/bao/uploaded/i1/2206479918978/O1CN018uvMW92GBySgyIic7_!!0-item_pic.jpg_480x480Q75',
        'https://gw.alicdn.com/bao/uploaded/i2/2206479918978/O1CN01N00v3R2GByRYeCD1v_!!0-item_pic.jpg_480x480Q75',
        'https://gw.alicdn.com/bao/uploaded/i1/3816165381/O1CN01Q4PHtO1pcXoQw3olL_!!0-item_pic.jpg_480x480Q75',
        'https://gw.alicdn.com/bao/uploaded/i4/3516851626/O1CN01ur82BD1NskYinadJE_!!0-item_pic.jpg_480x480Q75',
        'https://gw.alicdn.com/bao/uploaded/i3/3524443782/O1CN01bjNnGk1doCU6iys5B_!!0-item_pic.jpg_480x480Q75',
        'https://gw.alicdn.com/bao/uploaded/i1/2206617745862/O1CN01u1SACe1tAqK4BguQS_!!0-item_pic.jpg_480x480Q75',
        'https://gw.alicdn.com/bao/uploaded/i4/2201717159611/O1CN01c8hOq92Krt9eLzFVx_!!0-item_pic.jpg_480x480Q75'
      ]
    };
  },
  onLoad(option) {
    console.log(option);
  },
};
</script>

<style scoped lang="scss">
  .swiper {
    width: 100%;
    height: 320px;
    .swiper-image {
      width: 100%;
      height: 100%;
    }
  }
</style>
