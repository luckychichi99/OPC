<template>
  <view class="service-card-section">
    <view class="service-card" @click="handleServiceClick">
      <view class="card-content">
        <view class="service-icon">
          ☎️
        </view>
        <view class="service-text">
          <text class="service-title">一键联系人工客服</text>
          <text class="service-desc">专业顾问帮您解答所有问题</text>
        </view>
      </view>
      <view class="service-arrow">
        ›
      </view>
    </view>
  </view>
</template>

<script lang="ts" setup>
import { useToast } from 'wot-design-uni'

defineOptions({
  name: 'ServiceCard',
})

const toast = useToast()

function handleServiceClick() {
  console.log('点击联系人工客服')
  // TODO: 导航到客服页面或打开客服对话
  toast.info('客服功能开发中')
}
</script>

<style lang="scss" scoped>
.service-card-section {
  padding: 0 20rpx 20rpx;
  margin-top: -70rpx;
  position: relative;
  z-index: 10;
}

.service-card {
  background: white;
  border-radius: 24rpx;
  padding: 28rpx 24rpx;
  display: flex;
  align-items: center;
  justify-content: space-between;
  box-shadow: 0 10rpx 30rpx rgba(0, 0, 0, 0.1);
  transition: transform 0.2s;

  &:active {
    transform: scale(0.98);
  }
}

.card-content {
  display: flex;
  align-items: center;
  flex: 1;
  gap: 15rpx;
}

.service-icon {
  width: 80rpx;
  height: 80rpx;
  background: linear-gradient(135deg, #ffb86c 0%, #ffa540 100%);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 40rpx;
  flex-shrink: 0;
}

.service-text {
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.service-title {
  font-size: 30rpx;
  font-weight: 600;
  color: #333;
  margin-bottom: 8rpx;
  display: block;
}

.service-desc {
  font-size: 24rpx;
  color: #999;
  display: block;
}

.service-arrow {
  font-size: 40rpx;
  color: #ccc;
  margin-left: 10rpx;
  flex-shrink: 0;
}
</style>
