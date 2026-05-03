<template>
  <view class="warning-banner">
    <view class="warning-icon">
      ⚠️
    </view>
    <view class="warning-content">
      <text class="warning-title">注意！小心快招陷阱</text>
      <text class="warning-desc">很多品牌是骗人的，先做评估再决定！</text>
    </view>
  </view>
</template>

<script lang="ts" setup>
defineOptions({
  name: 'WarningBanner',
})
</script>

<style lang="scss" scoped>
.warning-banner {
  margin: 20rpx 20rpx;
  background: white;
  border-radius: 20rpx;
  padding: 25rpx;
  display: flex;
  align-items: flex-start;
  gap: 15rpx;
  box-shadow: 0 2rpx 8rpx rgba(0, 0, 0, 0.06);
}

.warning-icon {
  font-size: 40rpx;
  flex-shrink: 0;
  margin-top: 5rpx;
}

.warning-content {
  display: flex;
  flex-direction: column;
  flex: 1;
}

.warning-title {
  font-size: 30rpx;
  font-weight: 600;
  color: #333;
  margin-bottom: 8rpx;
  display: block;
}

.warning-desc {
  font-size: 24rpx;
  color: #666;
  line-height: 1.5;
  display: block;
}
</style>
