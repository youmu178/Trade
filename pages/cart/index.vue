<template>
  <view class="body">
    <van-submit-bar :loading="submitLoading" :price="money" button-text="提交订单" @submit="onSubmit">
      <label class="radio" @click="onCheck">
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
      allCheck: false
    };
  },
  methods: {
    onSubmit() {
      this.submitLoading = true;
      setTimeout(() => {
        this.submitLoading = false;
      }, 1000);
    },
    onCheck() {
      this.allCheck = !this.allCheck;
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
  & ::v-deep {
    // .van-submit-bar__bar {
    //   margin-bottom: 1px;
    // }
  }
}
.radio {
  display: flex;
  align-items: center;
}
</style>
