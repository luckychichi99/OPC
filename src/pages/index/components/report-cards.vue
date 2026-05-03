<template>
  <view class="report-cards-section">
    <view class="cards-grid">
      <!-- 报告示例 -->
      <view class="report-example-card" @click="handleReportExampleClick">
        <view class="card-icon">
          📋
        </view>
        <text class="card-title">报告示例</text>
        <text class="card-desc">查看报告样式</text>
      </view>

      <!-- 生成报告 -->
      <view class="generate-report-card" @click="handleGenerateReportClick">
        <view class="card-icon">
          ⭐
        </view>
        <text class="card-title">生成报告</text>
        <text class="card-desc">开始品牌评估</text>
      </view>
    </view>
  </view>
</template>

<script lang="ts" setup>
import { useToast } from 'wot-design-uni'

defineOptions({
  name: 'ReportCards',
})

const toast = useToast()

function handleReportExampleClick() {
  console.log('点击报告示例')
  toast.info('报告示例功能开发中')
}

function handleGenerateReportClick() {
  console.log('点击生成报告')
  toast.info('生成报告功能开发中')
}
</script>

<style lang="scss" scoped>
.report-cards-section {
  padding: 20rpx 20rpx;
}

.cards-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 20rpx;
}

.report-example-card {
  background: white;
  border-radius: 20rpx;
  padding: 40rpx 20rpx;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  border: 2rpx dashed #d0d0d0;
  transition: transform 0.2s;

  &:active {
    transform: scale(0.95);
  }
}

.generate-report-card {
  background: linear-gradient(135deg, #4a90ff 0%, #6baeff 100%);
  border-radius: 20rpx;
  padding: 40rpx 20rpx;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  color: white;
  box-shadow: 0 4rpx 16rpx rgba(0, 0, 0, 0.1);
  transition: transform 0.2s;

  &:active {
    transform: scale(0.95);
  }
}

.card-icon {
  font-size: 70rpx;
  margin-bottom: 20rpx;
}

.card-title {
  font-size: 30rpx;
  font-weight: 600;
  display: block;
  margin-bottom: 10rpx;
  color: inherit;
}

.card-desc {
  font-size: 24rpx;
  display: block;
  opacity: 0.85;
  color: inherit;
}

.report-example-card .card-title,
.report-example-card .card-desc {
  color: #333;
}
</style>
