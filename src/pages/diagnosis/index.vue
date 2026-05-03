<template>
  <view class="yd-page-container">
    <!-- 顶部导航栏 -->
    <wd-navbar
      title="诊断结果"
      placeholder
      safe-area-inset-top
      fixed
    />

    <!-- 页面内容 -->
    <scroll-view class="diagnosis-content" scroll-y>
      <!-- 诊断报告中心 -->
      <view class="report-center-card">
        <view class="report-icon">
          📄
        </view>
        <view class="report-text">
          <text class="report-title">诊断报告中心</text>
          <text class="report-desc">查看您历次的评估报告</text>
        </view>
      </view>

      <!-- 报告类型卡片 -->
      <view class="report-types-grid">
        <view
          v-for="item in reportTypes"
          :key="item.id"
          class="report-type-card"
          @click="handleReportClick(item)"
        >
          <view class="report-type-icon">
            {{ item.icon }}
          </view>
          <text class="report-type-title">{{ item.title }}</text>
          <text class="report-type-desc">{{ item.desc }}</text>
        </view>
      </view>

      <!-- 人工客服记录 -->
      <view class="service-record-card" @click="handleServiceRecordClick">
        <view class="service-record-icon">
          💬
        </view>
        <view class="service-record-content">
          <text class="service-record-title">人工客服记录</text>
          <text class="service-record-desc">历次人工沟通记录</text>
        </view>
        <view class="service-record-arrow">
          ›
        </view>
      </view>

      <!-- 一对一专家咨询 -->
      <view class="expert-consult-card" @click="handleExpertConsultClick">
        <view class="expert-icon">
          ✏️
        </view>
        <view class="expert-content">
          <text class="expert-title">一对一专家咨询</text>
          <text class="expert-desc">付费服务、专家为您深度分析</text>
        </view>
        <view class="expert-arrow">
          ›
        </view>
      </view>

      <!-- 底部安全区域 -->
      <view class="h-40rpx" />
    </scroll-view>

    <!-- 浮动电话按钮 -->
    <view class="floating-phone-button" @click="handlePhoneClick">
      <view class="phone-icon i-carbon-phone" />
    </view>
  </view>
</template>

<script lang="ts" setup>
import { useToast } from 'wot-design-uni'

defineOptions({
  name: 'DiagnosisPage',
})

definePage({
  style: {
    navigationStyle: 'custom',
  },
})

const toast = useToast()

interface ReportType {
  id: string
  icon: string
  title: string
  desc: string
}

const reportTypes: ReportType[] = [
  {
    id: 'startup',
    icon: '⭐',
    title: '创业评估报告',
    desc: '历次生成的报告',
  },
  {
    id: 'brand',
    icon: '👥',
    title: '品牌评估报告',
    desc: '历次生成的报告',
  },
  {
    id: 'location',
    icon: '📍',
    title: '选址评估报告',
    desc: '历次生成的报告',
  },
  {
    id: 'expert',
    icon: '👑',
    title: '专家咨询记录',
    desc: '与专家沟通记录',
  },
]

function handleReportClick(item: ReportType) {
  console.log('点击了', item.title)
  toast.info(`${item.title}功能开发中`)
}

function handleServiceRecordClick() {
  console.log('点击人工客服记录')
  toast.info('人工客服记录功能开发中')
}

function handleExpertConsultClick() {
  console.log('点击一对一专家咨询')
  toast.info('一对一专家咨询功能开发中')
}

function handlePhoneClick() {
  console.log('点击电话按钮')
  toast.info('客服功能开发中')
}
</script>

<style lang="scss" scoped>
.yd-page-container {
  min-height: 100vh;
  background: #f5f7fa;
}

.diagnosis-content {
  padding-top: 120rpx;
  padding-bottom: 100rpx;
}

.report-center-card {
  background: linear-gradient(135deg, #4a90ff 0%, #6baeff 100%);
  margin: 20rpx 20rpx;
  padding: 30rpx;
  border-radius: 20rpx;
  display: flex;
  align-items: center;
  gap: 20rpx;
  color: white;
  box-shadow: 0 4rpx 16rpx rgba(0, 0, 0, 0.1);
}

.report-icon {
  font-size: 50rpx;
  flex-shrink: 0;
}

.report-text {
  display: flex;
  flex-direction: column;
  flex: 1;
}

.report-title {
  font-size: 32rpx;
  font-weight: 600;
  display: block;
  margin-bottom: 8rpx;
}

.report-desc {
  font-size: 24rpx;
  opacity: 0.9;
  display: block;
}

.report-types-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 20rpx;
  padding: 20rpx;
  margin-top: 10rpx;
}

.report-type-card {
  background: white;
  border-radius: 20rpx;
  padding: 30rpx 20rpx;
  text-align: center;
  box-shadow: 0 2rpx 8rpx rgba(0, 0, 0, 0.06);
  transition: transform 0.2s;

  &:active {
    transform: scale(0.95);
  }
}

.report-type-icon {
  font-size: 60rpx;
  margin-bottom: 15rpx;
  display: block;
}

.report-type-title {
  font-size: 28rpx;
  font-weight: 600;
  color: #333;
  display: block;
  margin-bottom: 8rpx;
}

.report-type-desc {
  font-size: 22rpx;
  color: #999;
  display: block;
}

.service-record-card {
  background: white;
  margin: 20rpx 20rpx;
  padding: 25rpx 20rpx;
  border-radius: 20rpx;
  display: flex;
  align-items: center;
  gap: 15rpx;
  box-shadow: 0 2rpx 8rpx rgba(0, 0, 0, 0.06);
  transition: transform 0.2s;

  &:active {
    transform: scale(0.98);
  }
}

.service-record-icon {
  width: 80rpx;
  height: 80rpx;
  background: #e8f0ff;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 40rpx;
  flex-shrink: 0;
}

.service-record-content {
  display: flex;
  flex-direction: column;
  flex: 1;
}

.service-record-title {
  font-size: 30rpx;
  font-weight: 600;
  color: #333;
  display: block;
  margin-bottom: 8rpx;
}

.service-record-desc {
  font-size: 24rpx;
  color: #999;
  display: block;
}

.service-record-arrow {
  font-size: 40rpx;
  color: #ccc;
  flex-shrink: 0;
}

.expert-consult-card {
  background: linear-gradient(135deg, #b347d1 0%, #d16fd2 100%);
  margin: 20rpx 20rpx;
  padding: 30rpx 20rpx;
  border-radius: 20rpx;
  display: flex;
  align-items: center;
  gap: 15rpx;
  color: white;
  box-shadow: 0 4rpx 16rpx rgba(0, 0, 0, 0.1);
  transition: transform 0.2s;

  &:active {
    transform: scale(0.98);
  }
}

.expert-icon {
  width: 80rpx;
  height: 80rpx;
  background: rgba(255, 255, 255, 0.2);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 40rpx;
  flex-shrink: 0;
}

.expert-content {
  display: flex;
  flex-direction: column;
  flex: 1;
}

.expert-title {
  font-size: 30rpx;
  font-weight: 600;
  display: block;
  margin-bottom: 8rpx;
}

.expert-desc {
  font-size: 24rpx;
  opacity: 0.9;
  display: block;
}

.expert-arrow {
  font-size: 40rpx;
  opacity: 0.6;
  flex-shrink: 0;
}

.h-40rpx {
  height: 40rpx;
}

.floating-phone-button {
  position: fixed;
  bottom: 140rpx;
  right: 20rpx;
  width: 100rpx;
  height: 100rpx;
  border-radius: 50%;
  background: linear-gradient(135deg, #00d084 0%, #00a368 100%);
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0 8rpx 24rpx rgba(0, 208, 132, 0.4);
  z-index: 99;
  transition:
    transform 0.2s,
    box-shadow 0.2s;
}

.floating-phone-button:active {
  transform: scale(0.9);
  box-shadow: 0 4rpx 12rpx rgba(0, 208, 132, 0.3);
}

.phone-icon {
  font-size: 50rpx;
  color: white;
}
</style>
