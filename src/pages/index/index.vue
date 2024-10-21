<script lang="ts" setup>
const statusBarHeightValue = ref(20)
const topBarHeight = computed(() => statusBarHeightValue.value + 44)
const menuButtonLeft = ref(281)
onLoad(() => {
  const res = uni.getSystemInfoSync()
  statusBarHeightValue.value = res.statusBarHeight as number
  const menuButtonInfo = uni.getMenuButtonBoundingClientRect()
  menuButtonLeft.value = menuButtonInfo.left
})
</script>

<template>
  <view class="fixed left-0 top-0 -z-10 size-full backdrop-blur" />
  <image src="/src/static/img/bg.jpg" class="fixed left-0 top-0 -z-20 size-full" />
  <view class="text-gray-700" :style="{ height: `${topBarHeight}px` }">
    <view :style="{ height: `${statusBarHeightValue}px` }" />
    <view
      class="flex h-[44px] items-center justify-between pl-4 pr-2"
      :style="{ width: `${menuButtonLeft}px` }"
    >
      <view class="flex items-center gap-2">
        <view class="i-mdi-arrow-back text-xl" />
        <view>2/10</view>
      </view>
      <view class="flex items-center justify-end gap-2">
        <view class="i-mdi-star-outline text-xl" />
        <view class="i-mdi-trash-can-outline text-xl" />
        <view class="i-solar-menu-dots-bold text-xl" />
      </view>
    </view>
  </view>
  <view class="mt-[30px] px-4">
    <view class="text-3xl font-bold">
      吃饭
    </view>
    <view class="my-2 text-base font-thin text-gray-900">
      /chī , fàn/
    </view>
    <view class="mt-[30px] w-full rounded-xl bg-white/20 p-4 text-base backdrop-blur-md">
      <view>
        你<text class="font-bold">
          吃饭
        </text>了吗？
      </view>
      <view class="">
        have you had meals?
      </view>
    </view>
    <view class="mt-[30px] w-full rounded-xl bg-white/50 p-4 text-base backdrop-blur-md">
      In China and most countries in the world, eating is a kind of culture, and food is the priority of the people. Generally, three meals a day are divided into breakfast, lunch and dinner. Nowadays, in many large and medium-sized cities, many people have formed the habit of eating late night snacks. Eating is the main way that people ingest negative entropy to maintain the dissipative system.
    </view>
    <view class="mt-[20px] grid w-full grid-cols-3">
      <view class="flex flex-col items-center justify-center gap-0.5">
        <view>Know</view>
        <view class="h-1 w-4 rounded-full bg-green-400" />
      </view>
      <view class="flex flex-col items-center justify-center gap-0.5">
        <view>Blur</view>
        <view class="h-1 w-4 rounded-full bg-yellow-400" />
      </view>
      <view class="flex flex-col items-center justify-center gap-0.5">
        <view>Forget</view>
        <view class="h-1 w-4 rounded-full bg-red-400" />
      </view>
    </view>
  </view>
</template>
