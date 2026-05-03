<template>
  <view class="assessment-section">
    <view class="section-header">
      <text class="section-title">智能创业评估</text>
      <text class="section-subtitle">科学评估您的创业适配度</text>
    </view>

    <view class="assessment-description">
      通过4大维度全面评估您的餐饮创业条件，生成个性化建议报告
    </view>

    <view class="cards-grid">
      <view
        v-for="card in assessmentCards"
        :key="card.id"
        class="assessment-card"
        @click="handleCardClick(card)"
      >
        <view class="card-icon">
          {{ card.icon }}
        </view>
        <text class="card-title">{{ card.title }}</text>
        <text class="card-desc">{{ card.desc }}</text>
      </view>
    </view>
  </view>
</template>

<script lang="ts" setup>
defineOptions({
  name: 'AssessmentCards',
})

interface AssessmentCard {
  id: string
  icon: string
  title: string
  desc: string
}

const assessmentCards: AssessmentCard[] = [
  {
    id: 'fund',
    icon: '💰',
    title: '资金评估',
    desc: '评估您的资金准备',
  },
  {
    id: 'experience',
    icon: '📊',
    title: '经验评估',
    desc: '评估您的行业经验',
  },
  {
    id: 'time',
    icon: '⏰',
    title: '时间评估',
    desc: '评估您的时间投入',
  },
  {
    id: 'area',
    icon: '📍',
    title: '区域评估',
    desc: '评估您的选址条件',
  },
]

function handleCardClick(card: AssessmentCard) {
  console.log('点击了', card.title)
  // TODO: 处理点击事件，导航到具体评估页面
}
</script>

<style lang="scss" scoped>
.assessment-section {
  margin: 40rpx 20rpx;
}

.section-header {
  display: flex;
  flex-direction: column;
  margin-bottom: 20rpx;
}

.section-title {
  font-size: 36rpx;
  font-weight: 600;
  color: #333;
  margin-bottom: 10rpx;
}

.section-subtitle {
  font-size: 26rpx;
  color: #999;
  font-weight: 500;
}

.assessment-description {
  font-size: 26rpx;
  color: #666;
  margin-bottom: 30rpx;
  line-height: 1.5;
}

.cards-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 20rpx;
}

.assessment-card {
  background: white;
  border-radius: 20rpx;
  padding: 30rpx;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  box-shadow: 0 2rpx 8rpx rgba(0, 0, 0, 0.08);
  transition: transform 0.2s;

  &:active {
    transform: scale(0.95);
  }
}

.card-icon {
  font-size: 60rpx;
  margin-bottom: 15rpx;
}

.card-title {
  font-size: 28rpx;
  font-weight: 600;
  color: #333;
  margin-bottom: 8rpx;
}

.card-desc {
  font-size: 24rpx;
  color: #999;
  line-height: 1.4;
}
</style>
