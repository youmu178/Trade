<template>
  <view class="body">
    <button type="primary" @click="onSeletAddress">选择地址</button>
    <van-action-sheet :show="show" :round="round" :close-on-click-overlay="closeOverlay">
      <van-area :area-list="areaList" :columns-placeholder="columnsPlaceholder" @confirm="onAreaConfirm" @cancel="onAreaCancel" />
    </van-action-sheet>
  </view>
</template>

<script>
import areaList from './utils/area.js';
export default {
  data() {
    return {
      areaList: {},
      show: false,
      round: false,
      closeOverlay: true,
      columnsPlaceholder: ['请选择', '请选择', '请选择']
    };
  },
  onLoad(option) {
    // const goods = JSON.parse(decodeURIComponent(option.detail));
    this.areaList = areaList;
  },
  methods: {
    onSeletAddress() {
      this.show = true;
    },
    onAreaConfirm() {
      this.show = false;
    },
    onAreaCancel() {
      this.show = false;
    },
    onSubmit() {
      // this.submitLoading = true;
      // setTimeout(() => {
      //   this.submitLoading = false;
      // }, 1000);
    }
  }
};
</script>

<style scoped lang="scss">
.body {
  & ::v-deep {
    .van-picker__cancel {
      color: #494949;
    }
    .van-picker__confirm {
      color: #f50000;
    }
  }
}
</style>
