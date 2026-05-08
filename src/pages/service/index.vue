<template>
  <view class="service-page">
    <wd-navbar title="人工客服" placeholder safe-area-inset-top fixed />

    <view class="service-head-card">
      <view class="service-avatar">
        客
      </view>
      <view class="service-head-info">
        <text class="service-name">客服小王</text>
        <view class="service-status">
          <view class="status-dot" />
          <text class="status-text">在线</text>
        </view>
      </view>
    </view>

    <scroll-view class="service-content" scroll-y scroll-with-animation :scroll-top="0">
      <view class="chat-list">
        <view
          v-for="item in messages"
          :key="item.id"
          class="chat-message" :class="[item.role]"
        >
          <text>{{ item.text }}</text>
        </view>
      </view>

      <view class="quick-help-section">
        <text class="quick-help-title">快捷问题（点一下直接问）</text>
        <view class="quick-help-list">
          <view
            v-for="question in quickQuestions"
            :key="question.id"
            class="quick-help-item"
            @click="handleQuestionClick(question)"
          >
            <text>{{ question.text }}</text>
          </view>
        </view>
      </view>

      <view class="h-260rpx" />
    </scroll-view>

    <view class="chat-bottom-panel">
      <view class="input-row">
        <input
          v-model="message"
          class="message-input"
          type="text"
          placeholder="输入您的问题..."
          @confirm="sendMessage"
        >
        <view class="send-button" @click="sendMessage">
          <text class="send-icon">➤</text>
        </view>
      </view>

      <view class="bottom-shortcuts">
        <view
          v-for="question in quickQuestions.slice(0, 4)"
          :key="question.id"
          class="shortcut-chip"
          @click="handleQuestionClick(question)"
        >
          <text>{{ question.text }}</text>
        </view>
      </view>
    </view>
  </view>
</template>

<script lang="ts" setup>
import { ref } from 'vue'
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

interface QuickQuestion {
  id: string
  icon: string
  text: string
}

interface ChatMessage {
  id: string
  role: 'agent' | 'user'
  text: string
}

const quickQuestions: QuickQuestion[] = [
  { id: 'tea', icon: '🧋', text: '我想开奶茶店' },
  { id: 'cost', icon: '💰', text: '加盟要多少钱' },
  { id: 'brand', icon: '👥', text: '哪个品牌好' },
  { id: 'location', icon: '📍', text: '选址怎么选' },
  { id: 'trap', icon: '⚠️', text: '要避开的坑' },
  { id: 'other', icon: '❓', text: '其他问题' },
]

const messages = ref<ChatMessage[]>([
  {
    id: 'm1',
    role: 'agent',
    text: '您好！我是投必盈的客服顾问，请问有什么可以帮助您的？',
  },
])

const message = ref('')

function handleQuestionClick(question: QuickQuestion) {
  const content = question.text.trim()
  if (!content) {
    return
  }
  messages.value.push({ id: `user-${Date.now()}`, role: 'user', text: content })
  toast.success(`已发送问题：${content}`)
  setTimeout(() => {
    messages.value.push({
      id: `agent-${Date.now()}`,
      role: 'agent',
      text: '已收到，我们的客服顾问马上为您解答。',
    })
  }, 600)
}

function sendMessage() {
  const content = message.value.trim()
  if (!content) {
    toast.info('请输入您的问题')
    return
  }
  messages.value.push({ id: `user-${Date.now()}`, role: 'user', text: content })
  message.value = ''
  setTimeout(() => {
    messages.value.push({
      id: `agent-${Date.now()}`,
      role: 'agent',
      text: '您的问题已收到，我们会尽快回复您。',
    })
  }, 600)
}
</script>

<style lang="scss" scoped>
.service-page {
  min-height: 100vh;
  background: #f5f7fa;
}

.service-head-card {
  margin: 20rpx;
  margin-top: 120rpx;
  padding: 24rpx 24rpx 18rpx;
  border-radius: 30rpx;
  background: #ffffff;
  display: flex;
  align-items: center;
  gap: 20rpx;
  box-shadow: 0 10rpx 30rpx rgba(0, 0, 0, 0.05);
}

.service-avatar {
  width: 100rpx;
  height: 100rpx;
  border-radius: 50%;
  background: #00d084;
  color: white;
  font-size: 28rpx;
  font-weight: 700;
  display: flex;
  align-items: center;
  justify-content: center;
}

.service-head-info {
  display: flex;
  flex-direction: column;
}

.service-name {
  font-size: 32rpx;
  font-weight: 700;
  color: #111;
}

.service-status {
  margin-top: 10rpx;
  display: flex;
  align-items: center;
  gap: 10rpx;
}

.status-dot {
  width: 16rpx;
  height: 16rpx;
  background: #00d084;
  border-radius: 50%;
}

.status-text {
  color: #00b070;
  font-size: 24rpx;
}

.service-content {
  padding: 20rpx;
  padding-bottom: 260rpx;
}

.chat-list {
  display: flex;
  flex-direction: column;
  gap: 20rpx;
}

.chat-message {
  max-width: 80%;
  padding: 24rpx;
  border-radius: 30rpx;
  line-height: 1.7;
  font-size: 28rpx;
  box-shadow: 0 8rpx 20rpx rgba(0, 0, 0, 0.04);
}

.chat-message.agent {
  align-self: flex-start;
  background: #ffffff;
  border-bottom-left-radius: 8rpx;
}

.chat-message.user {
  align-self: flex-end;
  background: #d9f7ec;
  border-bottom-right-radius: 8rpx;
}

.quick-help-section {
  margin-top: 20rpx;
}

.quick-help-title {
  font-size: 28rpx;
  font-weight: 600;
  color: #333;
  margin-bottom: 18rpx;
}

.quick-help-list {
  display: flex;
  flex-wrap: wrap;
  gap: 14rpx;
}

.quick-help-item {
  background: white;
  border-radius: 50rpx;
  padding: 18rpx 24rpx;
  font-size: 24rpx;
  color: #333;
  box-shadow: 0 8rpx 20rpx rgba(0, 0, 0, 0.04);
}

.chat-bottom-panel {
  position: fixed;
  left: 0;
  right: 0;
  bottom: 0;
  padding: 18rpx 18rpx env(safe-area-inset-bottom, 20rpx);
  background: rgba(245, 247, 250, 0.98);
  box-shadow: 0 -2rpx 12rpx rgba(0, 0, 0, 0.08);
}

.input-row {
  display: flex;
  align-items: center;
  gap: 14rpx;
  margin-bottom: 18rpx;
}

.message-input {
  flex: 1;
  height: 84rpx;
  padding: 0 24rpx;
  border-radius: 50rpx;
  background: #ffffff;
  border: 1rpx solid #e7ebf0;
  font-size: 26rpx;
  color: #333;
}

.send-button {
  width: 88rpx;
  height: 88rpx;
  border-radius: 50%;
  background: #2b6cff;
  display: flex;
  align-items: center;
  justify-content: center;
}

.send-icon {
  color: #fff;
  font-size: 32rpx;
}

.bottom-shortcuts {
  display: flex;
  flex-wrap: wrap;
  gap: 12rpx;
}

.shortcut-chip {
  padding: 16rpx 20rpx;
  border-radius: 50rpx;
  background: white;
  font-size: 24rpx;
  color: #333;
  box-shadow: 0 8rpx 20rpx rgba(0, 0, 0, 0.04);
}

.h-260rpx {
  height: 260rpx;
}
</style>
