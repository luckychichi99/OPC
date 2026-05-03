<template>
  <view class="yd-page-container">
    <!-- 顶部导航栏 -->
    <wd-navbar
      title="投必盈"
      placeholder
      safe-area-inset-top
      fixed
    />

    <!-- 页面内容 -->
    <scroll-view class="knowledge-content" scroll-y>
      <!-- 今日必读 -->
      <view class="today-must-read-card">
        <view class="today-icon">
          🔥
        </view>
        <view class="today-content">
          <text class="today-title">今日必读</text>
          <text class="today-desc">加盟防骗指南：识别快招陷阱的10个信号</text>
          <text class="today-subtitle">90%的人都踩过这些坑，看完再也不怕被忽悠</text>
          <view class="today-button" @click="handleTodayClick">
            立即阅读
          </view>
        </view>
      </view>

      <!-- 标签页选项 -->
      <view class="tabs-container">
        <scroll-view class="tabs-scroll" scroll-x>
          <view
            v-for="tab in tabs"
            :key="tab.id"
            class="tab-item"
            :class="{ active: activeTab === tab.id }"
            @click="activeTab = tab.id"
          >
            {{ tab.label }}
          </view>
        </scroll-view>
      </view>

      <!-- 知识列表 -->
      <view class="knowledge-list">
        <view
          v-for="item in filteredKnowledge"
          :key="item.id"
          class="knowledge-item"
          @click="handleKnowledgeClick(item)"
        >
          <view class="knowledge-icon">
            {{ item.icon }}
          </view>
          <view class="knowledge-info">
            <view class="knowledge-top">
              <view class="knowledge-category-badge">
                {{ item.category }}
              </view>
            </view>
            <text class="knowledge-title">{{ item.title }}</text>
            <text class="knowledge-desc">{{ item.desc }}</text>
            <view class="knowledge-stats">
              <text class="stat-item">
                <text class="stat-icon">👁</text>
                <text class="stat-number">{{ item.views }}</text>
              </text>
              <text class="stat-item">
                <text class="stat-icon">♡</text>
                <text class="stat-number">{{ item.likes }}</text>
              </text>
            </view>
          </view>
        </view>
      </view>

      <!-- 加载更多按钮 -->
      <view class="load-more-section">
        <view class="load-more-button" @click="handleLoadMore">
          加载更多
        </view>
      </view>

      <!-- 底部安全区域 -->
      <view class="h-100rpx" />
    </scroll-view>

    <!-- 浮动电话按钮 -->
    <view class="floating-phone-button" @click="handlePhoneClick">
      <view class="phone-icon i-carbon-phone" />
    </view>
  </view>
</template>

<script lang="ts" setup>
import { computed, ref } from 'vue'
import { useToast } from 'wot-design-uni'

defineOptions({
  name: 'KnowledgePage',
})

definePage({
  style: {
    navigationStyle: 'custom',
  },
})

const toast = useToast()

const activeTab = ref('all')

interface Tab {
  id: string
  label: string
}

interface KnowledgeItem {
  id: string
  icon: string
  title: string
  category: string
  categoryId: string
  desc: string
  views: string
  likes: string
}

const tabs: Tab[] = [
  { id: 'all', label: '全部' },
  { id: 'fraud', label: '防骗指南' },
  { id: 'investment', label: '投资必读' },
  { id: 'location', label: '选址技巧' },
  { id: 'beginner', label: '新手必读' },
  { id: 'brand', label: '品牌选择' },
]

const knowledgeList: KnowledgeItem[] = [
  {
    id: '1',
    icon: '📚',
    title: '加盟前必须知道的5件事',
    category: '防骗指南',
    categoryId: 'fraud',
    desc: '避免被坑必看',
    views: '2.3万',
    likes: '856',
  },
  {
    id: '2',
    icon: '💰',
    title: '奶茶店投资预算详解',
    category: '投资必读',
    categoryId: 'investment',
    desc: '从几万到几十万，不同档次花多少钱',
    views: '1.8万',
    likes: '623',
  },
  {
    id: '3',
    icon: '✅',
    title: '如何识别正规加盟品牌',
    category: '品牌选择',
    categoryId: 'brand',
    desc: '查资质、看合同、问老店、三步搞定',
    views: '1.5万',
    likes: '445',
  },
  {
    id: '4',
    icon: '📍',
    title: '选址的10个黄金法则',
    category: '选址技巧',
    categoryId: 'location',
    desc: '人流量、竞争、租金、三点如何平衡',
    views: '3.1万',
    likes: '1023',
  },
  {
    id: '5',
    icon: '📋',
    title: '合同里的7个陷阱',
    category: '防骗指南',
    categoryId: 'fraud',
    desc: '很多人签完才后悔，看完避免踩坑',
    views: '1.2万',
    likes: '378',
  },
  {
    id: '6',
    icon: '⚠️',
    title: '新手开店的6个常见错误',
    category: '新手必读',
    categoryId: 'beginner',
    desc: '90%的新手都犯过，看完这个完全避免',
    views: '2.8万',
    likes: '756',
  },
]

const filteredKnowledge = computed(() => {
  if (activeTab.value === 'all') {
    return knowledgeList
  }
  return knowledgeList.filter(item => item.categoryId === activeTab.value)
})

function handleTodayClick() {
  console.log('点击今日必读')
  toast.info('文章详情页面开发中')
}

function handleKnowledgeClick(item: KnowledgeItem) {
  console.log('点击了', item.title)
  toast.info('文章详情页面开发中')
}

function handleLoadMore() {
  console.log('加载更多')
  toast.info('加载更多功能开发中')
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
  position: relative;
}

.knowledge-content {
  padding-top: 120rpx;
  padding-bottom: 140rpx;
}

.today-must-read-card {
  background: linear-gradient(135deg, #4a90ff 0%, #6baeff 100%);
  margin: 20rpx 20rpx;
  padding: 40rpx;
  border-radius: 20rpx;
  display: flex;
  gap: 20rpx;
  color: white;
  box-shadow: 0 4rpx 16rpx rgba(0, 0, 0, 0.1);
  min-height: 320rpx;
  justify-content: center;
}

.today-icon {
  font-size: 80rpx;
  flex-shrink: 0;
  display: flex;
  align-items: flex-start;
  margin-top: 10rpx;
}

.today-content {
  display: flex;
  flex-direction: column;
  flex: 1;
  justify-content: center;
}

.today-title {
  font-size: 32rpx;
  font-weight: 600;
  display: block;
  margin-bottom: 16rpx;
}

.today-desc {
  font-size: 28rpx;
  opacity: 1;
  display: block;
  margin-bottom: 12rpx;
  font-weight: 500;
  line-height: 1.4;
}

.today-subtitle {
  font-size: 24rpx;
  opacity: 0.9;
  display: block;
  margin-bottom: 20rpx;
  line-height: 1.4;
}

.today-button {
  background: white;
  color: #4a90ff;
  padding: 12rpx 30rpx;
  border-radius: 999rpx;
  font-size: 26rpx;
  font-weight: 600;
  text-align: center;
  display: inline-block;
  width: fit-content;
}

.tabs-container {
  margin-top: 0;
  background: white;
  border-bottom: 1rpx solid #eee;
  padding: 20rpx 0;
}

.tabs-scroll {
  display: flex;
  overflow-x: auto;
  padding: 0 20rpx;
  height: auto;
  white-space: nowrap;
  gap: 12rpx;

  &::-webkit-scrollbar {
    display: none;
  }
}

.tab-item {
  display: inline-flex;
  align-items: center;
  padding: 10rpx 24rpx;
  font-size: 26rpx;
  color: #333;
  font-weight: 500;
  white-space: nowrap;
  background: white;
  border: 1rpx solid #f0f0f0;
  border-radius: 999rpx;
  transition: all 0.2s;
  flex-shrink: 0;

  &.active {
    color: white;
    font-weight: 600;
    background: #4a90ff;
    border-color: #4a90ff;
  }
}

.knowledge-list {
  padding: 0 20rpx;
  margin-top: 20rpx;
}

.knowledge-item {
  background: white;
  border-radius: 16rpx;
  padding: 25rpx;
  margin-bottom: 20rpx;
  display: flex;
  gap: 15rpx;
  align-items: flex-start;
  box-shadow: 0 2rpx 8rpx rgba(0, 0, 0, 0.06);
  transition: transform 0.2s;

  &:active {
    transform: scale(0.98);
  }
}

.knowledge-icon {
  font-size: 50rpx;
  flex-shrink: 0;
  width: 70rpx;
  height: 70rpx;
  display: flex;
  align-items: center;
  justify-content: center;
  background: #f0f5ff;
  border-radius: 16rpx;
}

.knowledge-info {
  flex: 1;
  display: flex;
  flex-direction: column;
  min-width: 0;
}

.knowledge-top {
  display: flex;
  align-items: center;
  margin-bottom: 8rpx;
}

.knowledge-category-badge {
  display: inline-block;
  background: #4a90ff;
  color: white;
  padding: 4rpx 12rpx;
  border-radius: 12rpx;
  font-size: 20rpx;
  font-weight: 600;
}

.knowledge-title {
  font-size: 30rpx;
  font-weight: 600;
  color: #333;
  display: block;
  margin-bottom: 8rpx;
  word-break: break-word;
  line-height: 1.3;
}

.knowledge-desc {
  font-size: 24rpx;
  color: #999999;
  display: block;
  margin-bottom: 10rpx;
  line-height: 1.4;
}

.knowledge-stats {
  display: flex;
  gap: 16rpx;
  align-items: center;
}

.stat-item {
  display: flex;
  align-items: center;
  gap: 4rpx;
  font-size: 20rpx;
  color: #d0d0d0;
}

.stat-icon {
  color: #bbb;
  font-size: 20rpx;
}

.stat-number {
  color: #999;
  font-size: 20rpx;
}

.load-more-section {
  padding: 30rpx 20rpx;
  text-align: center;
}

.load-more-button {
  display: inline-block;
  padding: 12rpx 40rpx;
  border: 1rpx solid #ddd;
  border-radius: 20rpx;
  background: white;
  color: #999;
  font-size: 26rpx;
  transition: all 0.2s;
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

  &:active {
    transform: scale(0.9);
    box-shadow: 0 4rpx 12rpx rgba(0, 208, 132, 0.3);
  }
}

.phone-icon {
  font-size: 50rpx;
  color: white;
}

.h-100rpx {
  height: 100rpx;
}
</style>
