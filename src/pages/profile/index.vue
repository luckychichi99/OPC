<template>
  <view class="profile-page">
    <!-- 顶部导航栏 -->
    <wd-navbar
      title="我的"
      placeholder
      safe-area-inset-top
      fixed
    />

    <!-- 页面内容 -->
    <scroll-view class="profile-content" scroll-y>
      <!-- 用户信息卡片 -->
      <view class="user-info-card">
        <view class="user-avatar">
          <text class="avatar-icon">👤</text>
        </view>
        <view class="user-text">
          <text class="user-name">游客用户</text>
          <text class="user-desc">登录查看更多信息</text>
        </view>
      </view>

      <!-- 菜单项目列表 -->
      <view class="menu-list">
        <view
          v-for="item in menuItems"
          :key="item.id"
          class="menu-item"
          @click="handleMenuItemClick(item)"
        >
          <view class="menu-item-left">
            <view class="menu-item-icon" :style="{ color: item.color }">
              {{ item.icon }}
            </view>
            <text class="menu-item-title">{{ item.title }}</text>
          </view>
          <view class="menu-item-arrow">
            ›
          </view>
        </view>
      </view>

      <!-- 底部间距 -->
      <view class="h-120rpx" />
    </scroll-view>

    <!-- 浮动电话按钮 -->
    <view class="floating-phone-button" @click="handlePhoneClick">
      <view class="phone-icon i-carbon-phone" />
    </view>
  </view>
</template>

<script lang="ts" setup>
import { useToast } from 'wot-design-uni'

defineOptions({
  name: 'ProfilePage',
})

definePage({
  style: {
    navigationStyle: 'custom',
  },
})

const toast = useToast()

interface MenuItem {
  id: string
  icon: string
  title: string
  color: string
}

const menuItems: MenuItem[] = [
  {
    id: 'diagnosis',
    icon: '📄',
    title: '诊断结果',
    color: '#4a90ff',
  },
  {
    id: 'assessment',
    icon: '⭐',
    title: '我的评估',
    color: '#ffb856',
  },
  {
    id: 'favorite-brand',
    icon: '👥',
    title: '收藏的品牌',
    color: '#2ec7a6',
  },
  {
    id: 'favorite',
    icon: '📖',
    title: '我的收藏',
    color: '#b46bd9',
  },
]

function handleMenuItemClick(item: MenuItem) {
  console.log('点击了', item.title)
  if (item.id === 'diagnosis') {
    uni.switchTab({ url: '/pages/diagnosis/index' })
  } else {
    toast.info(`${item.title}功能开发中`)
  }
}

function handlePhoneClick() {
  console.log('点击电话按钮')
  toast.info('客服功能开发中')
}
</script>

<style lang="scss" scoped>
.profile-page {
  min-height: 100vh;
  background: #f5f7fa;
  position: relative;
}

.profile-content {
  padding-top: 120rpx;
  padding-bottom: 140rpx;
}

.user-info-card {
  background: white;
  margin: 20rpx 20rpx;
  padding: 30rpx;
  border-radius: 20rpx;
  display: flex;
  align-items: center;
  gap: 25rpx;
  box-shadow: 0 2rpx 8rpx rgba(0, 0, 0, 0.06);
}

.user-avatar {
  width: 120rpx;
  height: 120rpx;
  border-radius: 50%;
  overflow: hidden;
  flex-shrink: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  background: linear-gradient(135deg, #4a90ff 0%, #6baeff 100%);
}

.avatar-icon {
  font-size: 70rpx;
  color: white;
}

.user-text {
  flex: 1;
  display: flex;
  flex-direction: column;
}

.user-name {
  font-size: 30rpx;
  font-weight: 600;
  color: #333;
  display: block;
  margin-bottom: 8rpx;
}

.user-desc {
  font-size: 24rpx;
  color: #999;
  display: block;
}

.menu-list {
  background: white;
  margin: 20rpx 20rpx;
  border-radius: 20rpx;
  overflow: hidden;
  box-shadow: 0 2rpx 8rpx rgba(0, 0, 0, 0.06);
}

.menu-item {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 25rpx 30rpx;
  border-bottom: 1rpx solid #f0f0f0;
  transition: background-color 0.2s;

  &:last-child {
    border-bottom: none;
  }

  &:active {
    background-color: #f9f9f9;
  }
}

.menu-item-left {
  display: flex;
  align-items: center;
  gap: 15rpx;
  flex: 1;
}

.menu-item-icon {
  font-size: 40rpx;
  width: 50rpx;
  height: 50rpx;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
}

.menu-item-title {
  font-size: 30rpx;
  font-weight: 500;
  color: #333;
  display: block;
}

.menu-item-arrow {
  font-size: 40rpx;
  color: #d0d0d0;
  flex-shrink: 0;
  margin-left: 10rpx;
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

.h-120rpx {
  height: 120rpx;
}
</style>
