<script lang="ts" setup>
import TopBar from '@/components/TopBar.vue'
</script>

<template>
  <image src="/src/static/img/bg3.jpg" class="fixed left-0 top-0 -z-20 size-full" />
  <TopBar :show-menu="true" />
  <view class="mt-[10px] px-4">
    <view class="flex w-full flex-col justify-center gap-1  rounded-xl bg-white/20  p-2 backdrop-blur-md">
      <view class="text-sm font-bold  text-green-900 ">
        小又:
      </view>
      <view class="text-sm ">
        Please ask me some questions.
      </view>
    </view>
    <view class="my-[30px] flex w-full flex-col justify-center  gap-1 rounded-xl  bg-white/20 p-2 backdrop-blur-md">
      <view class="flex justify-end text-sm  font-bold ">
        My questions:
      </view>
      <view class="flex items-center justify-end gap-2  rounded-xl p-2">
        <view class="pinyin ">
          中国的四大文明是什么
        </view>
      </view>
    </view>
    <view class="item-center flex w-full flex-col justify-center gap-1 rounded-xl bg-white/20  p-2 backdrop-blur-md">
      <view class="text-sm font-bold  text-green-900 ">
        小又:
      </view>
      <view class="text-sm  ">
        The Four Great Inventions of China are:
      </view>
      <view class="text-sm ">
        1.Papermaking  2.Printing
      </view>
      <view class="text-sm">
        3.Gunpowder 4.The Compass
      </view>
    </view>
    <view class="my-[30px] flex w-full flex-col justify-center  gap-1 rounded-xl  bg-white/20 p-2 backdrop-blur-md">
      <view class="flex justify-end text-sm  font-bold ">
        My questions:
      </view>
      <view class="flex items-center justify-end gap-2  rounded-xl p-2">
        <view class="pinyin ">
          中国的国宝动物是什么？
        </view>
      </view>
    </view>
    <view class="flex w-full flex-col justify-center gap-1  rounded-xl bg-white/20  p-2 backdrop-blur-md">
      <view class="text-sm font-bold  text-green-900 ">
        小又:
      </view>
      <view class="text-sm">
        The national treasure animal of China is the giant panda.
      </view>
    </view>
    <view class="my-[30px] flex w-full flex-col justify-center  gap-1 rounded-xl  bg-white/20 p-2 backdrop-blur-md">
      <view class="flex justify-end text-sm  font-bold ">
        My questions:
      </view>
      <view class="flex items-center justify-end gap-2  rounded-xl p-2">
        <view class="pinyin ">
          中国的茶文化有哪些特点？
        </view>
      </view>
    </view>
    <view class="fixed bottom-[20rpx] left-[10rpx] z-50 px-[5rpx]">
      <view class=" flex h-[77rpx] w-[calc(100vw-40rpx)] items-center justify-center rounded-full bg-green-900/70 p-2 text-white backdrop-blur-sm">
        <view class="text-xs">
          Ask | How to comprehend the word?
        </view>
        <view class="flex items-center gap-1">
          <view class="i-mdi-search" />
          <view class="i-mdi-drag-vertical-variant" />
          <view class="i-mdi-camera" />
        </view>
      </view>
    </view>
  </view>
</template>
