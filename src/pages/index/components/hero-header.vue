<template>
  <view class="header-hero">
    <view class="hero-top">
      <view class="hero-avatar">
        <view class="hero-avatar-icon">
          🎯
        </view>
      </view>
      <view class="hero-text">
        <text class="hero-title">投必盈</text>
        <text class="hero-subtitle">帮您找到好项目</text>
      </view>
    </view>
  </view>
</template>

<script lang="ts" setup>
defineOptions({
  name: 'HeroHeader',
})
</script>

<style lang="scss" scoped>
.header-hero {
  background: linear-gradient(135deg, #3d79ff 0%, #5d9aff 100%);
  padding: 70rpx 20rpx 90rpx;
  border-radius: 0 0 32rpx 32rpx;
  position: relative;
  overflow: hidden;
}

.hero-top {
  display: flex;
  align-items: center;
  gap: 20rpx;
}

.hero-avatar {
  width: 120rpx;
  height: 120rpx;
  border-radius: 50%;
  background: white;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
}

.hero-avatar-icon {
  font-size: 48rpx;
}

.hero-text {
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.hero-title {
  font-size: 44rpx;
  font-weight: 700;
  color: white;
  display: block;
  margin-bottom: 10rpx;
}

.hero-subtitle {
  font-size: 26rpx;
  color: rgba(255, 255, 255, 0.88);
  display: block;
  line-height: 1.4;
}
</style>
