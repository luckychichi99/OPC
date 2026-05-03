<template>
  <view class="yd-page-container">
    <HeroHeader />

    <!-- 人工客服卡片 -->
    <ServiceCard />

    <!-- 功能卡片（创业评估、找品牌） -->
    <FeatureCards />

    <!-- 选址评估 -->
    <LocationAssessment />

    <!-- 警告提示 -->
    <WarningBanner />

    <!-- 热门知识 -->
    <PopularKnowledge />

    <!-- 浮动的绿色电话按钮 -->
    <view class="floating-phone-button" @click="handlePhoneClick">
      <view class="phone-icon i-carbon-phone" />
    </view>

    <!-- 底部安全区域 -->
    <view class="h-40rpx" />
  </view>
</template>

<script lang="ts" setup>
import { useToast } from 'wot-design-uni'
import FeatureCards from './components/feature-cards.vue'
import HeroHeader from './components/hero-header.vue'
import LocationAssessment from './components/location-assessment.vue'
import PopularKnowledge from './components/popular-knowledge.vue'
import ServiceCard from './components/service-card.vue'
import WarningBanner from './components/warning-banner.vue'

defineOptions({
  name: 'Home',
})

definePage({
  type: 'home',
  style: {
    navigationStyle: 'custom',
  },
})

const toast = useToast()

function handlePhoneClick() {
  console.log('点击绿色电话按钮')
  toast.info('客服功能开发中')
}
</script>

<style lang="scss" scoped>
.yd-page-container {
  min-height: 100vh;
  background: #f5f7fa;
}

.floating-phone-button {
  position: fixed;
  bottom: 120rpx;
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

  &:active {
    transform: scale(0.9);
    box-shadow: 0 4rpx 12rpx rgba(0, 208, 132, 0.3);
  }
}

.phone-icon {
  font-size: 50rpx;
  color: white;
}

.h-40rpx {
  height: 40rpx;
}
</style>
