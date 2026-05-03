<template>
  <view class="knowledge-section">
    <view class="knowledge-header">
      <view class="knowledge-header-icon">
        📖
      </view>      <text class="knowledge-title">热门知识</text>
      <text class="view-more" @click="handleViewMore">查看全部 ></text>
    </view>

    <view class="knowledge-list">
      <view
        v-for="item in knowledgeItems"
        :key="item.id"
        class="knowledge-item"
        @click="handleItemClick(item)"
      >
        <view class="item-icon">
          {{ item.icon }}
        </view>
        <view class="item-content">
          <text class="item-title">{{ item.title }}</text>
          <text class="item-meta">{{ item.readTime }}</text>
        </view>
        <view class="item-arrow">
          <text>></text>
        </view>
      </view>
    </view>
  </view>
</template>

<script lang="ts" setup>
defineOptions({
  name: 'PopularKnowledge',
})

interface KnowledgeItem {
  id: string
  icon: string
  title: string
  readTime: string
}

const knowledgeItems: KnowledgeItem[] = [
  {
    id: 'five-things',
    icon: '📚',
    title: '加盟前必须知道的5件事',
    readTime: '避免被坑必看',
  },
  {
    id: 'investment-guide',
    icon: '💰',
    title: '奶茶店投资预算详解',
    readTime: '新手必读',
  },
]

function handleItemClick(item: KnowledgeItem) {
  console.log('点击了', item.title)
  // 导航到知识详情页面
  uni.navigateTo({ url: '/pages/knowledge/index' })
}

function handleViewMore() {
  console.log('查看更多知识')
  // 导航到知识库页面
  uni.navigateTo({ url: '/pages/knowledge/index' })
}
</script>

<style lang="scss" scoped>
.knowledge-section {
  margin: 30rpx 20rpx;
}

.knowledge-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 25rpx;
}

.knowledge-header-icon {
  font-size: 38rpx;
  color: #4a90ff;
  margin-right: 12rpx;
}

.knowledge-title {
  font-size: 32rpx;
  font-weight: 600;
  color: #333;
}

.view-more {
  font-size: 26rpx;
  color: #5b6eff;
  font-weight: 500;
}

.knowledge-list {
  background: white;
  border-radius: 20rpx;
  overflow: hidden;
  box-shadow: 0 2rpx 8rpx rgba(0, 0, 0, 0.08);
}

.knowledge-item {
  display: flex;
  align-items: center;
  padding: 25rpx;
  border-bottom: 1rpx solid #f0f0f0;
  transition: background-color 0.2s;

  &:last-child {
    border-bottom: none;
  }

  &:active {
    background-color: #f9f9f9;
  }
}

.item-icon {
  font-size: 50rpx;
  margin-right: 15rpx;
  flex-shrink: 0;
}

.item-content {
  flex: 1;
  display: flex;
  flex-direction: column;
}

.item-title {
  font-size: 28rpx;
  font-weight: 500;
  color: #333;
  margin-bottom: 8rpx;
}

.item-meta {
  font-size: 24rpx;
  color: #999;
}

.item-arrow {
  font-size: 28rpx;
  color: #ccc;
  margin-left: 10rpx;
  flex-shrink: 0;
}
</style>
