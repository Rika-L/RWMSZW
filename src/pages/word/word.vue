<script lang="ts" setup>
import DYZItem from '@/components/DYZItem.vue'
import TopBar from '@/components/TopBar.vue'
import data from '@/main.json'

const wordIndex = ref(0)

const wordDetail = computed(() => {
  return data[wordIndex.value]
})

onLoad((options) => {
  wordIndex.value = options!.index as number
})
</script>

<template>
  <view class="fixed left-0 top-0 -z-10 size-full backdrop-blur" />
  <image src="/src/static/img/bg2.jpg" class="fixed left-0 top-0 -z-20 size-full" />
  <TopBar />
  <view class="mt-[30px] px-4">
    <view class="flex items-start gap-4">
      <view class="rounded-md bg-white/50 p-2 text-7xl text-gray-900">
        {{ wordDetail.chinese }}
      </view>
      <view class="flex flex-col gap-0.5">
        <view>Level:{{ wordDetail.level }}</view>
        <view>Radical:{{ wordDetail.radical }}</view>
        <view>Stroke:{{ wordDetail.strokes }}</view>
        <view>Structure:{{ wordDetail.structure }}</view>
      </view>
    </view>
    <view class="my-10 flex w-full flex-col gap-1 rounded-xl bg-white/20 p-4 backdrop-blur-md">
      <image src="/src/static/img/xin-stroke.png" mode="widthFix" />
      <view class="flex items-center justify-end text-gray-800">
        <text>Practice</text>
        <text class="i-mdi-arrow-right" />
      </view>
    </view>
    <DYZItem
      v-for="item in wordDetail.syllables"
      :key="item.spell"
      :spell="item.spell"
      :en-explain="item.enExplain"
      :zh-explain="item.zhExplain"
    />
  </view>
</template>
