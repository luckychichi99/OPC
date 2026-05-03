<template>
  <view class="service-page">
    <!-- 顶部导航栏 -->
    <wd-navbar
      title="人工服务"
      placeholder
      safe-area-inset-top
      fixed
    />

    <!-- 页面内容 -->
    <scroll-view class="service-content" scroll-y>
      <!-- 专业团队介绍卡片 -->
      <view class="team-card">
        <view class="team-icon">
          👥
        </view>
        <view class="team-content">
          <text class="team-title">专业顾问团队</text>
          <text class="team-desc">帮您解答所有问题</text>
        </view>

        <!-- checkmark列表 -->
        <view class="features-list">
          <view v-for="feature in teamFeatures" :key="feature" class="feature-item">
            <text class="feature-check">✓</text>
            <text class="feature-text">{{ feature }}</text>
          </view>
        </view>
      </view>

      <!-- 快捷问题区域 -->
      <view class="quick-questions-section">
        <text class="section-label">快捷问题（点一下直接问）</text>
        <view class="questions-grid">
          <view
            v-for="question in quickQuestions"
            :key="question.id"
            class="question-card"
            @click="handleQuestionClick(question)"
          >
            <text class="question-icon">{{ question.icon }}</text>
            <text class="question-text">{{ question.text }}</text>
          </view>
        </view>
      </view>

      <!-- 联系客服按钮 -->
      <view class="contact-button-section">
        <wd-button block type="success" size="large" @click="handleContactService">
          📞 立即联系人工客服
        </wd-button>
      </view>

      <!-- 服务时间 -->
      <view class="service-time">
        <text>服务时间：每天 9:00 - 21:00</text>
      </view>

      <!-- 底部间距 -->
      <view class="h-40rpx" />
    </scroll-view>
  </view>
</template>

<script lang="ts" setup>
import { useToast } from 'wot-design-uni'

defineOptions({
  name: 'ServicePage',
  style: {
    navigationStyle: 'custom',
  },
})

definePage({
  style: {
    navigationStyle: 'custom',
  },
})

const toast = useToast()

// 专业团队的特点
const teamFeatures = [
  '识别快招陷阱',
  '帮您选对品牌',
  '选址分析建议',
  '全程创业指导',
]

// 快捷问题列表
interface QuickQuestion {
  id: string
  icon: string
  text: string
}

const quickQuestions: QuickQuestion[] = [
  {
    id: 'tea',
    icon: '🧋',
    text: '我想开奶茶店',
  },
  {
    id: 'cost',
    icon: '💰',
    text: '加盟要多少钱',
  },
  {
    id: 'brand',
    icon: '👥',
    text: '哪个品牌好',
  },
  {
    id: 'location',
    icon: '📍',
    text: '选址怎么选',
  },
  {
    id: 'trap',
    icon: '⚠️',
    text: '要避开的坑',
  },
  {
    id: 'other',
    icon: '❓',
    text: '其他问题',
  },
]

function handleQuestionClick(question: QuickQuestion) {
  console.log('点击了快捷问题:', question.text)
  toast.success(`您的问题：${question.text}`)
}

function handleContactService() {
  console.log('联系人工客服')
  toast.success('正在为您连接人工客服...')
}
</script>

<style lang="scss" scoped>
.service-page {
  min-height: 100vh;
  background: #f5f7fa;
}

.service-content {
  padding-top: 120rpx;
  padding-bottom: 100rpx;
  min-height: 100vh;
}

// 专业团队卡片
.team-card {
  background: linear-gradient(135deg, #4080ff 0%, #5b9fff 100%);
  margin: 20rpx;
  padding: 40rpx 30rpx;
  border-radius: 30rpx;
  color: white;
}

.team-icon {
  font-size: 80rpx;
  text-align: center;
  margin-bottom: 20rpx;
  display: block;
}

.team-title {
  font-size: 36rpx;
  font-weight: 700;
  display: block;
  margin-bottom: 8rpx;
  text-align: center;
}

.team-desc {
  font-size: 26rpx;
  opacity: 0.95;
  display: block;
  text-align: center;
  margin-bottom: 30rpx;
}

// checkmark列表
.features-list {
  display: flex;
  flex-direction: column;
  gap: 16rpx;
}

.feature-item {
  display: flex;
  align-items: center;
  font-size: 26rpx;
}

.feature-check {
  color: #fff;
  margin-right: 12rpx;
  font-weight: bold;
  font-size: 30rpx;
}

.feature-text {
  flex: 1;
}

// 快捷问题区域
.quick-questions-section {
  padding: 30rpx 20rpx;
}

.section-label {
  font-size: 28rpx;
  font-weight: 600;
  color: #333;
  display: block;
  margin-bottom: 25rpx;
  padding: 0 20rpx;
}

.questions-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 15rpx;
}

.question-card {
  background: white;
  border-radius: 16rpx;
  padding: 25rpx 15rpx;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  box-shadow: 0 2rpx 8rpx rgba(0, 0, 0, 0.06);
  transition:
    transform 0.2s,
    box-shadow 0.2s;

  &:active {
    transform: scale(0.95);
    box-shadow: 0 4rpx 12rpx rgba(0, 0, 0, 0.12);
  }
}

.question-icon {
  font-size: 50rpx;
  margin-bottom: 12rpx;
  display: block;
}

.question-text {
  font-size: 24rpx;
  color: #333;
  font-weight: 500;
  line-height: 1.4;
}

// 联系客服按钮
.contact-button-section {
  padding: 30rpx 20rpx;

  :deep(.wd-button) {
    height: 100rpx;
    font-size: 32rpx;
    font-weight: 600;
    border-radius: 50rpx;
    background: linear-gradient(135deg, #2dc258 0%, #1db646 100%);
  }
}

// 服务时间
.service-time {
  text-align: center;
  padding: 20rpx;
  font-size: 26rpx;
  color: #999;
  margin-bottom: 40rpx;
}

.h-40rpx {
  height: 40rpx;
}
</style>
