<template>
  <view class="feature-cards-section">
    <view class="cards-grid">
      <view
        v-for="card in featureCards"
        :key="card.id"
        class="feature-card"
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
  name: 'FeatureCards',
})

interface FeatureCard {
  id: string
  icon: string
  title: string
  desc: string
}

const featureCards: FeatureCard[] = [
  {
    id: 'assessment',
    icon: '⭐',
    title: '创业评估',
    desc: '测测您适合创业吗',
  },
  {
    id: 'brand',
    icon: '👥',
    title: '找品牌',
    desc: '帮您匹配好品牌',
  },
]

function handleCardClick(card: FeatureCard) {
  console.log('点击了', card.title)
  if (card.id === 'assessment') {
    uni.navigateTo({ url: '/pages/evaluation/index' })
  } else if (card.id === 'brand') {
    uni.navigateTo({ url: '/pages/brand/index' })
  } else {
    uni.navigateTo({ url: '/pages/service/index' })
  }
}
</script>

<style lang="scss" scoped>
.feature-cards-section {
  padding: 20rpx 20rpx;
}

.cards-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 20rpx;
}

.feature-card {
  background: white;
  border-radius: 20rpx;
  padding: 40rpx 20rpx;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  box-shadow: 0 2rpx 8rpx rgba(0, 0, 0, 0.06);
  transition: transform 0.2s;

  &:active {
    transform: scale(0.95);
  }
}

.card-icon {
  font-size: 70rpx;
  margin-bottom: 20rpx;
  width: 100rpx;
  height: 100rpx;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 20rpx;
}

.feature-card:nth-child(1) .card-icon {
  background: #d5e1ff;
}

.feature-card:nth-child(2) .card-icon {
  background: #d0f0e8;
}

.card-title {
  font-size: 30rpx;
  font-weight: 600;
  color: #333;
  margin-bottom: 10rpx;
  display: block;
}

.card-desc {
  font-size: 24rpx;
  color: #999;
  line-height: 1.4;
  display: block;
}
</style>
