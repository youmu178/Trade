<template>
  <view class="body">
    <view class="head">
      <van-image width="36" height="36" fit="cover" round src="https://img.yzcdn.cn/vant/cat.jpeg" />
      <view class="shop-info">
        <text class="name">XXXX店铺</text>
        <text class="doorplate">B-101</text>
      </view>
    </view>
    <van-sticky>
      <view class="sort-tab">
        <text @click="zongheClick" :class="{ clickp: zhClick }">综合排序</text>
        <view class="tab-jiage">
          <text @click="jiageClick" :class="{ clickp: jgClick }">价格排序</text>
          <image :src="sortSrc" style="width: 5px; height: 10px;" />
        </view>
        <text @click="xiaoliangClick" :class="{ clickp: xlClick }">销量排序</text>
      </view>
    </van-sticky>
    <view class="list">
      <van-grid column-num="2" gutter="5">
        <van-grid-item use-slot v-for="item in img" :key="item.index" @click="itemClick(item)">
          <view class="item-img"><image class="img-" lazy-load mode="aspectFit" :src="item" /></view>
          <view class="jia">
            <text class="zhekoujia">¥ 99.00</text>
            <text class="yuanjia">¥ 999.00</text>
            <text class="zhekou">1折</text>
          </view>
          <text class="title">爵森马伯特男士春秋装上衣服潮流卫衣秋季男装男装男装</text>
        </van-grid-item>
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
      zhClick: true,
      xlClick: false,
      jgClick: false,
      isClickSort: false,
      sortSrc: require('@/static/search/ic_sort_default.png'),
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
    // this.onRefresh();
  },
  onShow() {},
  onPullDownRefresh() {},
  methods: {
    zongheClick() {
      this.zhClick = true;
      this.xlClick = false;
      this.jgClick = false;
      this.sortSrc = require('@/static/search/ic_sort_default.png');
      // this.sort = 1;
      this.onRefresh();
    },
    xiaoliangClick() {
      this.zhClick = false;
      this.xlClick = true;
      this.jgClick = false;
      this.sortSrc = require('@/static/search/ic_sort_default.png');
      // this.sort = 2;
      this.onRefresh();
    },
    jiageClick() {
      this.zhClick = false;
      this.xlClick = false;
      this.jgClick = true;
      this.isClickSort = !this.isClickSort;
      this.sortSrc = this.isClickSort ? require('@/static/search/ic_sort_desc.png') : require('@/static/search/ic_sort_asc.png');
      // this.sort = this.isClickSort ? 4 : 3;
      this.onRefresh();
    },
    itemClick(item) {
      let that = this;
      uni.navigateTo({
        url: '/pages/goods/detail'
      });
    },
    onRefresh() {},
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
page {
  background-color: #f5f5f5;
}
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
      background: rgba(255, 255, 255, 1) no-repeat;
      overflow: hidden;
      background-size: 100% 100%;
      border-radius: 4px;
    }
    .van-grid-item {
      // margin-top: 0px !important;
    }
    .van-grid-item__content--center {
      align-items: flex-start;
    }
  }
}
.head {
  display: flex;
  align-items: center;
  padding: 12px 0px 12px 8px;
  // margin-bottom: 5px;
  background-color: #ffffff;
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
.sort-tab {
  display: flex;
  align-items: center;
  justify-content: space-around;
  // margin-top: 5px;
  height: 40px;
  background: white;
  text {
    color: #232323;
  }
  .clickp {
    color: #f50000;
  }
  .tab-jiage {
    display: flex;
    align-items: center;
    image {
      margin-left: 5px;
    }
  }
}
.list {
  margin: 10px 5px;
  .item-img {
    width: 100%;
    height: 0px;
    padding-bottom: 100%;
    position: relative;
    .img- {
      width: 100%;
      height: 100%;
      position: absolute;
    }
  }
  .jia {
    display: flex;
    align-items: flex-end;
    margin: 5px 2px 0px 10px;
    .zhekoujia {
      color: #f50000;
      font-weight: 500;
      font-size: 16px;
    }
    .yuanjia {
      font-size: 12px;
      color: #9c9c9c;
      margin-left: 2px;
      text-decoration: line-through;
    }
    .zhekou {
      margin-left: 6px;
      margin-bottom: 1px;
      font-size: 10px;
      color: #f2ca00;
      border: solid 1px #ffd801;
      border-radius: 3px;
      padding: 0px 3px;
    }
  }
  .title {
    font-size: 14px;
    margin: 2px 5px 12px 6px;
    color: #3B3B3B;
    // font-weight:500;
    overflow: hidden;
    text-overflow: ellipsis;
    display: -webkit-box;
    -webkit-line-clamp: 2;
    -webkit-box-orient: vertical;
    word-break: break-all;
  }
}
</style>
