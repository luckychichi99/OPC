<template>
  <view class="brand-page">
    <wd-navbar
      title="品牌推荐"
      placeholder
      safe-area-inset-top
      fixed
    />

    <scroll-view class="brand-content" scroll-y>
      <view class="report-actions">
        <view class="report-card report-example-card" @click="handleReportExample">
          <view class="card-icon">
            📋
          </view>
          <text class="card-title">报告示例</text>
          <text class="card-desc">查看报告样式</text>
        </view>

        <view class="report-card report-generate-card" @click="handleGenerateReport">
          <view class="card-icon">
            ⭐
          </view>
          <text class="card-title report-title-primary">生成报告</text>
          <text class="card-desc report-desc-primary">开始品牌评估</text>
        </view>
      </view>

      <view class="recommend-banner">
        <view class="recommend-icon">
          ★
        </view>
        <view class="recommend-texts">
          <text class="recommend-banner-title">根据您的评估结果</text>
          <text class="recommend-banner-desc">为您推荐以下品牌</text>
        </view>
      </view>

      <view class="brand-list">
        <view v-for="item in brands" :key="item.id" class="brand-item">
          <view class="brand-left">
            <view class="brand-image-wrap">
              <image :src="item.image" class="brand-image" mode="aspectFill" />
            </view>
            <view class="brand-info">
              <view class="brand-info-top">
                <text class="brand-name">{{ item.name }}</text>
                <text v-if="item.tag" class="brand-tag">{{ item.tag }}</text>
              </view>
              <view class="brand-meta-row">
                <text class="brand-meta">匹配度 {{ item.match }}</text>
                <text class="brand-dot">·</text>
                <text class="brand-meta">{{ item.range }}</text>
              </view>
              <text class="brand-shops">{{ item.shops }}</text>
            </view>
          </view>
          <view class="brand-score-wrap">
            <text class="brand-score">{{ item.match }}</text>
            <text class="brand-score-label">匹配</text>
          </view>
        </view>
      </view>

      <view class="h-120rpx" />
    </scroll-view>
  </view>
</template>

<script lang="ts" setup>
import { ref } from 'vue'
import { useToast } from 'wot-design-uni'

const toast = useToast()

const brands = ref([
  {
    id: '1',
    name: '茶颜悦色',
    tag: '推荐',
    match: '92%',
    range: '15-30万',
    shops: '500+门店',
    image: '/static/images/brand-1.png',
  },
  {
    id: '2',
    name: '蜜雪冰城',
    tag: '热门',
    match: '85%',
    range: '8-15万',
    shops: '20000+门店',
    image: '/static/images/brand-2.png',
  },
  {
    id: '3',
    name: '喜茶',
    tag: '',
    match: '72%',
    range: '50万+',
    shops: '800+门店',
    image: '/static/images/brand-3.png',
  },
])

function handleReportExample() {
  toast.info('报告示例功能开发中')
}

function handleGenerateReport() {
  toast.info('生成报告功能开发中')
}
</script>

<style lang="scss" scoped>
.brand-page {
  min-height: 100vh;
  background: #f5f7fa;
}

.brand-content {
  padding-top: 120rpx;
}

.report-actions {
  display: flex;
  gap: 20rpx;
  padding: 0 20rpx;
}

.report-card {
  flex: 1;
  min-height: 220rpx;
  border-radius: 28rpx;
  padding: 28rpx 26rpx;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 16rpx;
  background: white;
  box-shadow: 0 10rpx 30rpx rgba(0, 0, 0, 0.05);
}

.report-example-card {
  border: 2rpx dashed #d8dde8;
}

.report-generate-card {
  box-shadow: 0 10rpx 30rpx rgba(64, 144, 255, 0.15);
}

.card-icon {
  width: 80rpx;
  height: 80rpx;
  border-radius: 22rpx;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 38rpx;
  color: #4a90ff;
  background: #f4f8ff;
}

.card-title {
  font-size: 28rpx;
  font-weight: 700;
  color: #222;
}

.card-desc {
  font-size: 24rpx;
  color: #8f9cb1;
}

.report-title-primary,
.report-desc-primary {
  color: #2b6cff;
}

.recommend-banner {
  margin: 20rpx;
  padding: 20rpx 22rpx;
  border-radius: 24rpx;
  background: white;
  display: flex;
  align-items: center;
  gap: 16rpx;
  box-shadow: 0 10rpx 30rpx rgba(0, 0, 0, 0.05);
}

.recommend-icon {
  width: 64rpx;
  height: 64rpx;
  border-radius: 18rpx;
  background: #eaf4ff;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 30rpx;
  color: #2b6cff;
}

.recommend-texts {
  flex: 1;
}

.recommend-banner-title {
  display: block;
  font-size: 26rpx;
  font-weight: 700;
  color: #1f2a3d;
  margin-bottom: 8rpx;
}

.recommend-banner-desc {
  display: block;
  font-size: 24rpx;
  color: #6f7d95;
}

.brand-list {
  padding: 0 20rpx;
  margin-top: 18rpx;
}

.brand-item {
  background: white;
  border-radius: 28rpx;
  padding: 24rpx;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 20rpx;
  margin-bottom: 16rpx;
  box-shadow: 0 10rpx 30rpx rgba(0, 0, 0, 0.05);
}

.brand-left {
  display: flex;
  align-items: center;
  gap: 18rpx;
  flex: 1;
}

.brand-image-wrap {
  width: 96rpx;
  height: 96rpx;
  border-radius: 24rpx;
  background: #eef4ff;
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
}

.brand-image {
  width: 100%;
  height: 100%;
}

.brand-info {
  display: flex;
  flex-direction: column;
  flex: 1;
}

.brand-info-top {
  display: flex;
  align-items: center;
  gap: 12rpx;
  margin-bottom: 10rpx;
}

.brand-name {
  font-size: 28rpx;
  font-weight: 700;
  color: #222;
}

.brand-tag {
  font-size: 20rpx;
  color: #ff9b00;
  background: rgba(255, 154, 0, 0.12);
  padding: 4rpx 12rpx;
  border-radius: 999rpx;
}

.brand-meta-row {
  display: flex;
  align-items: center;
  gap: 10rpx;
  margin-bottom: 8rpx;
}

.brand-meta {
  font-size: 22rpx;
  color: #8f9cb1;
}

.brand-dot {
  font-size: 22rpx;
  color: #c8d1de;
}

.brand-shops {
  font-size: 22rpx;
  color: #8f9cb1;
}

.brand-score-wrap {
  display: flex;
  flex-direction: column;
  align-items: flex-end;
  justify-content: center;
}

.brand-score {
  font-size: 32rpx;
  font-weight: 700;
  color: #2b6cff;
}

.brand-score-label {
  margin-top: 6rpx;
  font-size: 22rpx;
  color: #8f9cb1;
}

.h-120rpx {
  height: 120rpx;
}
</style>
