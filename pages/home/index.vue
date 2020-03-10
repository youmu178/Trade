<template>
  <view class="body">
    <!-- <van-overlay :show="show" z-index="99" @click="onClickHide">
      <view class="wrapper">
        <swiper class="swiper" circular :indicator-color="indicatorColor" :indicator-active-color="indicatorActiveColor">
          <swiper-item v-for="item in img" :key="item.index"><image :src="item" lazy-load mode="widthFix" class="swiper-image"></image></swiper-item>
        </swiper>
        <van-goods-action>
          <van-goods-action-icon icon="cart-o" text="购物车" bind:click="onClickIcon" />
          <van-goods-action-button text="加入购物车" type="warning" bind:click="onClickButton" />
          <van-goods-action-button text="立即购买" bind:click="onClickButton" />
        </van-goods-action>
      </view>
    </van-overlay> -->
    <view class="item" @click="itemClick(img)">
      <view class="head">
        <van-image width="36" height="36" fit="cover" round src="https://img.yzcdn.cn/vant/cat.jpeg" />
        <view class="shop-info">
          <text class="name">XXXX店铺</text>
          <text class="doorplate">B-101</text>
        </view>
      </view>
      <van-grid column-num="3" square :border="true" gutter="5">
        <van-grid-item use-slot v-for="item in img" :key="item.index"><image style="width: 100%;" lazy-load :src="item" /></van-grid-item>
      </van-grid>
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
  onLoad() {
    // this.getData();
  },
  onShow() {},
  onPullDownRefresh() {},
  methods: {
    itemClick(item) {
      let that = this;
      uni.navigateTo({
      	url: '/pages/goods/detail'
      });
      // uni.hideTabBar({
      //   animation: true,
      //   success() {
      //     that.swiperData = item;
      //     that.show = true;
      //   }
      // });
    },
    // onClickHide() {
    //   this.show = false;
    //   uni.showTabBar({
    //     animation: true
    //   });
    // },
    getData() {
      uniCloud
        .callFunction({
          name: 'goods',
          data: { a: 1 }
        })
        .then(res => {
          console.log(res.result);
        });
      //   let that = this;
      //   uni.request({
      //     url: 'https://wkbox.imsupercard.com/index/newIndex',
      //     header: {
      //       // "UUID":	'd703eaac-0b15-4414-a219-351e57fed3b2',
      //       appVer: 24,
      //       platform: 1,
      //       OSVer: 29
      //     },
      //     success: res => {
      //       let data = res.data;
      //       console.log(data);
      //       let topBannerList = data.data.topBannerList;
      //       if (topBannerList !== null && topBannerList.length > 0) {
      //         that.bannerData = topBannerList;
      //       }
      //     },
      //     fail: () => {},
      //     complete: () => {}
      //   });
    }
  }
};
</script>
<style>
/* page {
  background-color: #f5f5f5;
} */
</style>
<style scoped lang="scss">
.banner-item {
  height: 125px;
}
.banner-image {
  height: 125px;
  width: 100%;
}
.body {
  & ::v-deep {
    .van-grid-item__content {
      padding: 0px;
      // margin-top: 5px;
      // margin-right: 5px;
    }
    .van-grid-item {
      margin-top: 0px !important;
    }
  }
}
.wrapper {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  height: 100%;
  .swiper {
    width: 100%;
    height: 450px;
    .swiper-image {
      width: 100%;
      height: 100%;
    }
  }
  // .cart {
  //   display: flex;
  //   width: 100%;
  //   align-items: center;
  //   padding-left: 20px;
  //   .add {
  //     color: white;
  //     font-size: 18px;
  //     position: absolute;
  //     right: 10px;
  //   }
  // }
}
.item {
  background: #ffffff;
  border-radius: 8px;
  margin: 10px 10px 0px 10px;
  padding-bottom: 5px;
  overflow: hidden;
  .head {
    display: flex;
    align-items: center;
    padding: 12px 0px 12px 8px;
    margin-bottom: 5px;
    background: linear-gradient(270deg, rgba(253, 235, 229, 1) 0%, rgba(255, 223, 213, 1) 100%);
    .shop-info {
      display: flex;
      flex-direction: column;
      margin-left: 5px;
      .name {
        color: #232323;
        font-size: 15px;
      }
      .doorplate {
        color: #737373;
        font-size: 12px;
      }
    }
  }
}
</style>
