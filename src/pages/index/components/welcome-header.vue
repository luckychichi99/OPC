<template>
  <view class="welcome-header">
    <text class="welcome-text">欢迎使用</text>
    <text class="title">投必盈</text>
    <text class="subtitle">餐饮创业智能辅助平台</text>
  </view>
</template>

<script lang="ts" setup>
defineOptions({
  name: 'WelcomeHeader',
})
</script>

<style lang="scss" scoped>
.welcome-header {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 40rpx 20rpx;
  background: linear-gradient(135deg, #5b6eff 0%, #7b8dff 100%);
  color: white;
  text-align: center;
}

.welcome-text {
  font-size: 24rpx;
  opacity: 0.9;
  margin-bottom: 20rpx;
}

.title {
  font-size: 60rpx;
  font-weight: bold;
  line-height: 1;
  margin-bottom: 15rpx;
}

.subtitle {
  font-size: 28rpx;
  opacity: 0.95;
  font-weight: 500;
}
</style>
