<template>
  <view class="fraud-warning-section">
    <view class="warning-card">
      <view class="warning-header">
        <text class="warning-icon">⚠️</text>
        <text class="warning-title">快招陷阱预警</text>
      </view>
      <text class="warning-text">
        警惕！90%的餐饮创业失败者因信息不对称导致决策失误，远离快招陷阱，从评估开始。
      </text>
    </view>
  </view>
</template>

<script lang="ts" setup>
defineOptions({
  name: 'FraudWarning',
})
</script>

<style lang="scss" scoped>
.fraud-warning-section {
  margin: 30rpx 20rpx;
}

.warning-card {
  background: #fff7e6;
  border-radius: 20rpx;
  padding: 30rpx;
  border-left: 6rpx solid #ff9500;
}

.warning-header {
  display: flex;
  align-items: center;
  margin-bottom: 15rpx;
}

.warning-icon {
  font-size: 40rpx;
  margin-right: 12rpx;
}

.warning-title {
  font-size: 32rpx;
  font-weight: 600;
  color: #333;
}

.warning-text {
  font-size: 26rpx;
  color: #666;
  line-height: 1.6;
  display: block;
  margin-top: 10rpx;
}
</style>
