<template>
  <view class="result-page">
    <wd-navbar
      title="获取专属方案"
      placeholder
      safe-area-inset-top
      fixed
    />

    <scroll-view class="result-content" scroll-y>
      <view class="score-card">
        <text class="score-label">您的创业适配评分</text>
        <text class="score-value">75</text>
        <text class="score-tag">中度适配</text>
      </view>

      <view class="tip-card">
        <view class="tip-title">
          留下联系方式获取
        </view>
        <view class="tip-item">
          专业顾问为您定制专属创业方案
        </view>
        <view class="tip-item">
          免费获取详细品牌分析报告
        </view>
        <view class="tip-item">
          专属顾问1对1咨询服务
        </view>
        <view class="tip-item">
          最新热门项目第一时间推送
        </view>
      </view>

      <view class="form-card">
        <text class="form-label">请留下您的联系方式</text>
        <view class="form-field">
          <text class="field-label">您的称呼（选填）</text>
          <input
            v-model="name"
            class="input-box"
            placeholder="如：张先生、李女士"
          >
        </view>
        <view class="form-field">
          <text class="field-label">手机号 *</text>
          <input
            v-model="mobile"
            class="input-box"
            placeholder="请输入手机号"
            type="number"
            maxlength="11"
          >
        </view>
      </view>

      <view class="submit-button" @click="handleSubmit">
        <text class="submit-text">立即获取专属方案</text>
      </view>

      <view class="privacy-text">
        您的信息会受到严格保护，不会泄露给第三方
      </view>
      <view class="h-120rpx" />
    </scroll-view>
  </view>
</template>

<script lang="ts" setup>
import { ref } from 'vue'
import { useToast } from 'wot-design-uni'

const name = ref('')
const mobile = ref('')
const toast = useToast()

function handleSubmit() {
  if (!mobile.value) {
    uni.showToast({ title: '请输入手机号', icon: 'none' })
    return
  }

  toast.success('专属方案已提交，我们会尽快与您联系')
}
</script>

<style lang="scss" scoped>
.result-page {
  min-height: 100vh;
  background: #f5f7fa;
}

.result-content {
  padding-top: 120rpx;
  padding: 0 20rpx;
}

.score-card {
  background: linear-gradient(135deg, #3b79ff 0%, #4f9bff 100%);
  border-radius: 30rpx;
  padding: 40rpx 30rpx;
  margin-top: 20rpx;
  color: white;
  text-align: center;
  box-shadow: 0 10rpx 30rpx rgba(59, 121, 255, 0.2);
}

.score-label {
  font-size: 26rpx;
  opacity: 0.9;
  display: block;
  margin-bottom: 20rpx;
}

.score-value {
  font-size: 80rpx;
  font-weight: 700;
  display: block;
  margin-bottom: 18rpx;
}

.score-tag {
  font-size: 26rpx;
  background: rgba(255, 255, 255, 0.18);
  padding: 12rpx 24rpx;
  border-radius: 999rpx;
  display: inline-block;
}

.tip-card {
  background: white;
  border-radius: 30rpx;
  padding: 30rpx 25rpx;
  margin-top: 20rpx;
  box-shadow: 0 2rpx 12rpx rgba(0, 0, 0, 0.08);
}

.tip-title {
  font-size: 28rpx;
  font-weight: 600;
  color: #333;
  margin-bottom: 18rpx;
}

.tip-item {
  font-size: 24rpx;
  color: #666;
  line-height: 1.8;
}

.form-card {
  background: white;
  border-radius: 30rpx;
  padding: 30rpx 25rpx;
  margin-top: 20rpx;
  box-shadow: 0 2rpx 12rpx rgba(0, 0, 0, 0.08);
}

.form-label {
  display: block;
  font-size: 28rpx;
  font-weight: 600;
  color: #333;
  margin-bottom: 25rpx;
}

.form-field {
  margin-bottom: 24rpx;
}

.field-label {
  font-size: 24rpx;
  color: #999;
  display: block;
  margin-bottom: 16rpx;
}

.input-box {
  width: 100%;
  height: 84rpx;
  padding: 0 24rpx;
  border-radius: 20rpx;
  border: 1rpx solid #ececec;
  background: #f8f9fb;
  font-size: 28rpx;
  color: #333;
}

.submit-button {
  background: #00c968;
  border-radius: 24rpx;
  height: 100rpx;
  margin: 30rpx 0 10rpx;
  display: flex;
  align-items: center;
  justify-content: center;
}

.submit-text {
  font-size: 30rpx;
  color: white;
  font-weight: 700;
}

.privacy-text {
  font-size: 22rpx;
  color: #999;
  text-align: center;
  margin-bottom: 20rpx;
}

.h-120rpx {
  height: 120rpx;
}
</style>
