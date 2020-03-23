<template>
  <view class="body">
    <van-checkbox-group :value="checkBoxResult" @change="onChange">
      <view v-for="(item, index) in itemList" :key="item.index">
        <view class="item-goods" @click.stop="itemClick(item)" @touchstart="touchstart()" @touchend="touchend()">
          <view style="height: 50px; display: flex; align-items: center;" @click="onCheckClick">
            <van-checkbox :name="index" ref="checkboxes" checked-color="#f6411f"></van-checkbox>
          </view>
          <van-image class="image" width="94" height="94" :src="item.img" lazy-load fit="cover" />
          <view class="info">
            <text class="title">爵森马伯特男士春秋装上衣服潮流卫衣秋季男装男装男装</text>
            <text class="sort">XL 黑色</text>
            <view class="money-stepper">
              <text class="money">¥ 99.00</text>
              <van-stepper value="1" min="1" max="10" @change="onChangeNumber" class="number-stepper" />
            </view>
          </view>
        </view>
      </view>
    </van-checkbox-group>
    <van-dialog use-slot title="标题" :show="showDialog" show-cancel-button @close="onClose"></van-dialog>
    <van-submit-bar :loading="submitLoading" :price="money" button-text="提交订单" @submit="onSubmit">
      <label class="radio" @click="onAllCheck">
        <radio color="#f6411f" :checked="allCheck" />
        全选
      </label>
    </van-submit-bar>
  </view>
</template>

<script>
export default {
  data() {
    return {
      submitLoading: false,
      money: 3050,
      allCheck: false,
      checkBoxResult: [],
      timeOutEvent: 0,
      showDialog: false,
      list: [
        { img: 'https://gw.alicdn.com/bao/uploaded/i1/2206479918978/O1CN018uvMW92GBySgyIic7_!!0-item_pic.jpg_480x480Q75' },
        { img: 'https://gw.alicdn.com/bao/uploaded/i1/2206479918978/O1CN018uvMW92GBySgyIic7_!!0-item_pic.jpg_480x480Q75' },
        { img: 'https://gw.alicdn.com/bao/uploaded/i1/2206479918978/O1CN018uvMW92GBySgyIic7_!!0-item_pic.jpg_480x480Q75' },
        { img: 'https://gw.alicdn.com/bao/uploaded/i1/2206479918978/O1CN018uvMW92GBySgyIic7_!!0-item_pic.jpg_480x480Q75' },
        { img: 'https://gw.alicdn.com/bao/uploaded/i1/2206479918978/O1CN018uvMW92GBySgyIic7_!!0-item_pic.jpg_480x480Q75' },
        { img: 'https://gw.alicdn.com/bao/uploaded/i1/2206479918978/O1CN018uvMW92GBySgyIic7_!!0-item_pic.jpg_480x480Q75' }
      ]
    };
  },
  computed: {
    itemList() {
      this.list.forEach(item => {
        item.checked = false;
      });
      return this.list;
    }
  },
  methods: {
    onSubmit() {
      this.submitLoading = true;
      setTimeout(() => {
        this.submitLoading = false;
      }, 1000);
    },
    onChange(event) {
      console.log(event.detail);
      this.checkBoxResult = event.detail;
      this.allCheck = this.checkBoxResult.length == this.itemList.length;
    },
    onCheckClick(event) {
      // console.log(event.currentTarget.dataset);
      // console.log(this.$refs.checkboxes[index]);
    },
    onAllCheck() {
      this.allCheck = !this.allCheck;
      this.checkBoxResult = [];
      let result = [];
      if (this.allCheck) {
        this.itemList.forEach((item, index) => {
          result.push(index + '');
          this.checkBoxResult = result;
        });
      }
    },
    itemClick(item) {},
    touchstart() {
      this.timeOutEvent = setTimeout(() => {
        this.timeOutEvent = 0;
        this.showDialog = true;
      }, 500);
    },
    touchend() {
      clearTimeout(this.timeOutEvent);
      this.timeOutEvent = 0;
    },
    onClose() {
      this.showDialog = false;
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
  margin-bottom: 65px;
  & ::v-deep {
    // .van-submit-bar__bar {
    //   margin-bottom: 1px;
    // }
  }
}
.item-goods {
  display: flex;
  align-items: center;
  background-color: #ffffff;
  margin: 10px 10px 0px 10px;
  padding: 10px 15px 5px 15px;
  border-radius: 5px;
  .image {
    margin-left: 15px;
    margin-right: 10px;
    margin-bottom: 0px;
  }
  .info {
    display: flex;
    flex-direction: column;
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
      align-items: flex-end;
      margin-top: 10px;
      .money {
        color: #f6411f;
        font-size: 16px;
      }
      .number-stepper {
        position: absolute;
        right: 0px;
      }
    }
  }
}
.radio {
  display: flex;
  align-items: center;
}
</style>
