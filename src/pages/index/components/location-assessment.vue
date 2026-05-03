<template>
  <view class="location-assessment-section">
    <view class="assessment-card" @click="handleAssessmentClick">
      <view class="card-content">
        <view class="card-icon">
          📍
        </view>
        <view class="card-text">
          <text class="card-title">选址评估</text>
          <text class="card-desc">帮您找到最佳门店位置</text>
        </view>
      </view>
      <view class="card-arrow">
        ›
      </view>
    </view>
  </view>
</template>

<script lang="ts" setup>
import { useToast } from 'wot-design-uni'

defineOptions({
  name: 'LocationAssessment',
})

const toast = useToast()

function handleAssessmentClick() {
  console.log('点击选址评估')
  toast.info('选址评估功能开发中')
}
</script>

<style lang="scss" scoped>
.location-assessment-section {
  padding: 20rpx 20rpx;
}

.assessment-card {
  background: white;
  border-radius: 20rpx;
  padding: 25rpx 20rpx;
  display: flex;
  align-items: center;
  justify-content: space-between;
  box-shadow: 0 2rpx 8rpx rgba(0, 0, 0, 0.06);
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

.card-icon {
  width: 80rpx;
  height: 80rpx;
  background: linear-gradient(135deg, #4a90ff 0%, #6baeff 100%);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 40rpx;
  flex-shrink: 0;
}

.card-text {
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.card-title {
  font-size: 30rpx;
  font-weight: 600;
  color: #333;
  margin-bottom: 8rpx;
  display: block;
}

.card-desc {
  font-size: 24rpx;
  color: #999;
  display: block;
}

.card-arrow {
  font-size: 40rpx;
  color: #ccc;
  margin-left: 10rpx;
  flex-shrink: 0;
}
</style>
