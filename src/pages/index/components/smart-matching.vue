<template>
  <view class="matching-section">
    <view class="matching-grid">
      <view class="matching-card" @click="handleBrandClick">
        <view class="card-header">
          <image src="/static/images/brand-icon.png" class="card-image" />
          <view class="card-info">
            <text class="card-title">品牌智能匹配</text>
            <text class="card-subtitle">精准匹配适合您的餐饮品牌</text>
          </view>
        </view>
      </view>

      <view class="matching-card" @click="handleLocationClick">
        <view class="card-header">
          <image src="/static/images/location-icon.png" class="card-image" />
          <view class="card-info">
            <text class="card-title">智能选址建议</text>
            <text class="card-subtitle">科学推荐最佳门店位置</text>
          </view>
        </view>
      </view>
    </view>
  </view>
</template>

<script lang="ts" setup>
defineOptions({
  name: 'SmartMatching',
})

function handleBrandClick() {
  console.log('点击品牌智能匹配')
  // TODO: 导航到品牌匹配页面
}

function handleLocationClick() {
  console.log('点击智能选址建议')
  // TODO: 导航到智能选址页面
}
</script>

<style lang="scss" scoped>
.matching-section {
  margin: 30rpx 20rpx;
}

.matching-grid {
  display: flex;
  flex-direction: column;
  gap: 20rpx;
}

.matching-card {
  background: white;
  border-radius: 20rpx;
  padding: 25rpx;
  box-shadow: 0 2rpx 8rpx rgba(0, 0, 0, 0.08);
  transition: transform 0.2s;

  &:active {
    transform: scale(0.98);
  }
}

.card-header {
  display: flex;
  align-items: center;
  gap: 15rpx;
}

.card-image {
  width: 80rpx;
  height: 80rpx;
  border-radius: 12rpx;
  flex-shrink: 0;
}

.card-info {
  flex: 1;
  display: flex;
  flex-direction: column;
}

.card-title {
  font-size: 30rpx;
  font-weight: 600;
  color: #333;
  margin-bottom: 8rpx;
}

.card-subtitle {
  font-size: 24rpx;
  color: #999;
}
</style>
