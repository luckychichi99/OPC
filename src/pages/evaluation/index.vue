<template>
  <view class="evaluation-page">
    <wd-navbar
      title="创业评估"
      placeholder
      safe-area-inset-top
      fixed
    />

    <scroll-view class="content" scroll-y>
      <view class="page-body">
        <view class="progress-bar-wrapper">
          <text class="progress-text">第 {{ currentIndex + 1 }} / {{ questions.length }} 题</text>
          <view class="progress-bar">
            <view class="progress-fill" :style="{ width: progressWidth }" />
          </view>
        </view>

        <view class="question-card">
          <text class="question-title">{{ questions[currentIndex].title }}</text>
          <view class="options-list">
            <view
              v-for="option in questions[currentIndex].options"
              :key="option.id"
              class="option-item"
              :class="{ active: selectedOption === option.id }"
              @click="selectOption(option.id)"
            >
              <text class="option-text">{{ option.label }}</text>
            </view>
          </view>
        </view>

        <view class="action-button" @click="handleNext">
          <text class="action-text">{{ currentIndex < questions.length - 1 ? '下一步' : '查看结果' }}</text>
        </view>
      </view>

      <view class="h-120rpx" />
    </scroll-view>
  </view>
</template>

<script lang="ts" setup>
import { computed, ref } from 'vue'

interface Question {
  id: string
  title: string
  options: Array<{ id: string, label: string }>
}

const questions: Question[] = [
  {
    id: 'age',
    title: '您今年多大?',
    options: [
      { id: '20-25', label: '20-25岁' },
      { id: '26-30', label: '26-30岁' },
      { id: '31-35', label: '31-35岁' },
      { id: '35+', label: '35岁以上' },
    ],
  },
  {
    id: 'capital',
    title: '您想投资多少钱?',
    options: [
      { id: 'below-100', label: '10万以下' },
      { id: '100-300', label: '10-30万' },
      { id: '300-500', label: '30-50万' },
      { id: '500+', label: '50万以上' },
    ],
  },
  {
    id: 'time',
    title: '您有时间开店吗?',
    options: [
      { id: 'full-time', label: '全职做' },
      { id: 'part-time', label: '兼职做' },
      { id: 'unknown', label: '不确定' },
    ],
  },
  {
    id: 'experience',
    title: '您做过餐饮吗?',
    options: [
      { id: 'yes', label: '做过' },
      { id: 'no', label: '没做过' },
    ],
  },
]

const currentIndex = ref(0)
const selectedOption = ref('')
const answers = ref<Record<number, string>>({})

const progressWidth = computed(() => `${((currentIndex.value + 1) / questions.length) * 100}%`)

function selectOption(optionId: string) {
  selectedOption.value = optionId
  answers.value[currentIndex.value] = optionId
}

function handleNext() {
  if (!selectedOption.value) {
    uni.showToast({ title: '请选择一个选项', icon: 'none' })
    return
  }

  if (currentIndex.value < questions.length - 1) {
    currentIndex.value += 1
    selectedOption.value = answers.value[currentIndex.value] || ''
  } else {
    uni.navigateTo({ url: '/pages/evaluation/result/index' })
  }
}
</script>

<style lang="scss" scoped>
.evaluation-page {
  min-height: 100vh;
  background: #f5f7fa;
}

.content {
  padding-top: 120rpx;
}

.page-body {
  padding: 0 20rpx;
}

.progress-bar-wrapper {
  margin: 20rpx 0 30rpx;
}

.progress-text {
  font-size: 26rpx;
  color: #333;
  display: block;
  margin-bottom: 16rpx;
}

.progress-bar {
  width: 100%;
  height: 18rpx;
  border-radius: 9rpx;
  background: #e8e8e8;
  overflow: hidden;
}

.progress-fill {
  height: 100%;
  background: #2b6cff;
  border-radius: 9rpx;
}

.question-card {
  background: white;
  border-radius: 30rpx;
  padding: 40rpx 30rpx;
  box-shadow: 0 10rpx 30rpx rgba(0, 0, 0, 0.08);
}

.question-title {
  font-size: 34rpx;
  color: #111;
  font-weight: 700;
  display: block;
  margin-bottom: 40rpx;
  text-align: center;
}

.options-list {
  display: flex;
  flex-direction: column;
  gap: 20rpx;
}

.option-item {
  background: #f6f7fb;
  border-radius: 24rpx;
  padding: 30rpx 28rpx;
  transition:
    background-color 0.2s,
    color 0.2s;
}

.option-item.active {
  background: #2b6cff;
}

.option-text {
  font-size: 28rpx;
  color: #333;
}

.option-item.active .option-text {
  color: #ffffff;
}

.action-button {
  margin: 40rpx 0;
  background: #2b6cff;
  border-radius: 24rpx;
  height: 100rpx;
  display: flex;
  align-items: center;
  justify-content: center;
}

.action-text {
  font-size: 30rpx;
  color: white;
  font-weight: 600;
}

.h-120rpx {
  height: 120rpx;
}
</style>
