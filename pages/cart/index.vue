<template>
  <view class="body">
    <view v-for="(item, index) in itemList" :key="item.index">
      <view class="item-goods">
        <van-checkbox :value="item.checked" @change="onCheck" checked-color="#f6411f"></van-checkbox>
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
    onCheckClick(index) {
      console.log('----- ' + index);
      this.itemList.forEach((item, pos) => {
        console.log(pos);
        if (index == pos) {
          item.checked = true;
        }
        item.checked = true;
      });
    },
    onCheck(event) {
      // console.log(event);
      console.log(event.detail);
      // console.log(event.currentTarget.dataset);
      // this.itemList[0].checked = event.detail;
      // console.log(this.$refs.checkbox);
      // for (let pos in this.itemList) {
      //   if (index == pos) {
      //     // this.$refs.checkbox[index].toggle();
      //   }
      // }
      
      // console.log(this.$refs.checkbox[0].dataset);
      // this.itemList.forEach((item, pos) => {
      //   item.checked = true;
      // });
      this.itemList.forEach(item => {
        item.checked = event.detail;
      });
    },
    onAllCheck() {
      this.allCheck = !this.allCheck;
      this.itemList.forEach(item => {
        item.checked = this.allCheck;
      });
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
