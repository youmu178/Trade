<template>
  <view>
    <van-area :area-list="areaList" value="110101" />
  </view>
</template>

<script>
import areaList from './utils/area.js';
export default {
  data() {
    return {
      areaList : {}
    };
  },
  onLoad(option) {
    // const goods = JSON.parse(decodeURIComponent(option.detail));
    this.areaList = areaList;
  },
  methods: {
    onSubmit() {
      
      // this.submitLoading = true;
      // setTimeout(() => {
      //   this.submitLoading = false;
      // }, 1000);
    }
  }
};
</script>

<style scoped lang="scss"></style>
