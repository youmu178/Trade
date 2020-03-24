<template>
  <view class="content">
    <van-tabs :active="active" sticky animated swipeable :border="border" color="#f6411f" @change="onChange">
      <van-tab title="待付款">内容 1</van-tab>
      <van-tab title="已付款">内容 2</van-tab>
      <van-tab title="已发货">内容 3</van-tab>
      <van-tab title="已完成">内容 4</van-tab>
    </van-tabs>
  </view>
</template>

<script>
export default {
  data() {
    return {
      active: 0,
      border: false
    };
  },
  methods: {
    onChange(evnt) {}
  }
};
</script>
<style>
page {
  background-color: #f5f5f5;
}
</style>
<style scoped lang="scss">
.content {
}
</style>
