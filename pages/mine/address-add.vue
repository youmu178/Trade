<template>
  <view class="body">
    <view class="card">
      <view class="item">
        <text>姓名</text>
        <input placeholder="收货人姓名" />
      </view>
      <view class="line"></view>
      <view class="item">
        <text>电话</text>
        <input placeholder="收货人手机号" type="number" />
      </view>
      <view class="line"></view>
      <view class="item" @click="onSeletAddress">
        <text>地区</text>
        <input placeholder="选择省 / 市 / 区" disabled />
      </view>
      <view class="line"></view>
      <view class="item">
        <text>详细地址</text>
        <input placeholder="街道门牌 楼房房间号等信息" />
      </view>
    </view>
    <view class="card">
      <view class="item">
        <text class="switch-title">设为默认收货地址</text>
        <switch color="#f6411f" @change="switchChange" />
      </view>
    </view>

    <button class="button-ok" style="margin-top: 30px;" type="primary">提交</button>
    <button class="button-del">删除</button>
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
    switchChange(e) {
      console.log('switch1 发生 change 事件，携带值为', e.target.value);
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
<style>
page {
  background-color: #f5f5f5;
}
</style>
<style scoped lang="scss">
.body {
  padding-left: 15px;
  padding-right: 15px;
  & ::v-deep {
    .van-picker__cancel {
      color: #494949;
    }
    .van-picker__confirm {
      color: #f50000;
    }
  }
}
.card {
  background-color: #ffffff;
  border-radius: 5px;
  margin-top: 20px;
  padding-left: 12px;
  padding-right: 12px;
  .item {
    display: flex;
    align-items: center;
    height: 48px;
    text {
      width: 90px;
    }
    input {
      width: 100%;
      margin-left: 10px;
    }
    .switch-title {
      width: auto;
    }
    switch {
      position: absolute;
      right: 25px;
    }
  }
  .line {
    width: 100%;
    height: 1px;
    background-color: #f5f5f5;
  }
}
button {
  border-radius: 25px;
  margin-bottom: 15px;
}
button:after {
  border: 1px solid rgba(0, 0, 0, 0) !important;
}
.button-ok {
  background-color: #f6411f;
}

.button-del {
  background-color: #ffffff;
}
</style>
