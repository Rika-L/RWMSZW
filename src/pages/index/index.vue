<script lang="ts" setup>
import data from '@/main.json'

function hdlTap(index: number) {
  uni.navigateTo({
    url: `/pages/word/word?index=${index}`,

  })
}
</script>

<template>
  <view class="fixed left-0 top-0 -z-10 size-full backdrop-blur" />
  <image src="/src/static/img/bg2.jpg" class="fixed left-0 top-0 -z-20 size-full" />
  <div class=" relative mt-[100rpx] flex justify-center">
    <input type="text" class=" relative top-0 h-[70rpx] w-[430rpx] rounded-md bg-slate-200 pl-2 text-[26rpx] font-bold text-black opacity-75 shadow-inner shadow-[#888888]" placeholder="请输入想要搜索的文字" bindinput="inputChange">
    <div class=" absolute left-[607rpx] top-0 h-[70rpx] w-[91rpx] rounded-lg bg-inherit">
      <div class=" size-full rounded-lg bg-slate-600 opacity-55" />
      <text class=" absolute left-[10px] top-[19rpx] text-[26rpx] font-semibold" bindtap="search">
        搜索
      </text>
    </div>
  </div>
  <scroll-view
    class=" absolute ml-[90rpx] mt-[50rpx] flex h-[900rpx] w-[580rpx] flex-wrap" scroll-x="false" scroll-y="true"
  >
    <view
      v-for="(item, index) in data"
      :key="index"
      class=" relative left-[20rpx] mt-[30rpx] h-[150rpx] w-[560rpx] rounded-[30rpx] border-none bg-inherit"
      @tap="hdlTap(index)"
    >
      <div class="absolute h-full w-[550rpx] rounded-[30rpx] bg-slate-700 opacity-45" />
      <div class=" absolute left-[20rpx] top-[15rpx] size-[120rpx] rounded-[30rpx] bg-gray-200 opacity-75">
        <text class=" absolute  left-[18rpx] top-[-2rpx] text-[90rpx]" selectable="false" space="false" decode="false">
          {{ item.chinese }}
        </text>
      </div>
      <view class=" absolute left-[250rpx] top-[5rpx] mt-[28rpx] flex flex-col text-[30rpx]">
        <view>Level:{{ item.level }}</view>
        <view>Stroke:{{ item.strokes }}</view>
      </view>
    </view>
  </scroll-view>
</template>
