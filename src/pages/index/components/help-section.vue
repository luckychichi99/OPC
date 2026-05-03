<template>
  <view class="help-section">
    <text class="section-title">我们能帮您做什么</text>

    <view class="help-grid">
      <view
        v-for="item in helpItems"
        :key="item.id"
        class="help-item"
      >
        <view class="item-icon">
          {{ item.icon }}
        </view>
        <text class="item-title">{{ item.title }}</text>
      </view>
    </view>
  </view>
</template>

<script lang="ts" setup>
defineOptions({
  name: 'HelpSection',
})

interface HelpItem {
  id: string
  icon: string
  title: string
}

const helpItems: HelpItem[] = [
  {
    id: 'fund',
    icon: '💰',
    title: '资金评估',
  },
  {
    id: 'time',
    icon: '⏰',
    title: '时间评估',
  },
  {
    id: 'location',
    icon: '📍',
    title: '选址建议',
  },
  {
    id: 'service',
    icon: '👨‍💼',
    title: '人工咨询',
  },
]
</script>

<style lang="scss" scoped>
.help-section {
  padding: 40rpx 20rpx;
}

.section-title {
  font-size: 36rpx;
  font-weight: 600;
  color: #333;
  display: block;
  margin-bottom: 40rpx;
}

.help-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 30rpx;
}

.help-item {
  text-align: center;
}

.item-icon {
  width: 100rpx;
  height: 100rpx;
  margin: 0 auto 20rpx;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 50rpx;
  background: #f0f5ff;
  border-radius: 20rpx;
}

.item-title {
  font-size: 28rpx;
  font-weight: 500;
  color: #333;
  display: block;
}
</style>
