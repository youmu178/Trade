<template>
  <view class="content">
    <van-cell title="获取微信收货地址" is-link clickable @click="onWxClick" />
    <view class="address-list" v-show="showList">
      <van-cell :title="itemName" :label="itemAddress" clickable center is-link>
        <view slot="right-icon" style="width: 40px; height: 40px; ">
          <van-icon name="edit" />
         </view>
      </van-cell>
    </view>

    <van-button class="add" color="#f6411f" block @click="onAdd">新增收货地址</van-button>
  </view>
</template>

<script>
// import New from '';
export default {
  data() {
    return {
      itemName: '',
      itemAddress: '',
      showList: false
    };
  },
  onLoad(option) {
    // const goods = JSON.parse(decodeURIComponent(option.detail));
  },
  methods: {
    onWxClick() {
      let that = this;
      uni.chooseAddress({
        success(res) {
          console.log(res.userName + ', ' + res.telNumber);
          console.log('收货地址：' + res.provinceName + res.cityName + res.countyName + res.detailInfo);
          that.itemName = res.userName + ', ' + res.telNumber;
          that.itemAddress = '收货地址：' + res.provinceName + res.cityName + res.countyName + res.detailInfo;
          that.showList = true;
        }
      });
    },
    onAdd() {
      uni.navigateTo({
        url: '/pages/mine/address-add'
      });
    }
  }
};
</script>

<style scoped lang="scss">
.content {
  .address-list {
    margin-top: 15px;
  }
  .add {
    position: fixed;
    bottom: 0;
    width: 100%;
  }
}
</style>
