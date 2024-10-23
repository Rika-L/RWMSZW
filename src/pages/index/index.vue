<script lang="ts" setup>
import data from '@/main.json'

const keyword = ref('') // 定义keyword变量
const filteredData = ref(data) // 存储过滤后的数据

function filterData() {
  if (!keyword.value) {
    filteredData.value = data // 如果keyword为空，重置数据
  }
  else {
    filteredData.value = data.filter(item => item.chinese.includes(keyword.value)) // 过滤数据
  }
}

watchEffect(() => {
  if (!keyword.value) {
    filteredData.value = data
  }
})

function hdlTap(index: number) {
  uni.navigateTo({
    url: `/pages/word/word?index=${index}`,

  })
}
</script>

<template>
  <view class="fixed left-0 top-0 -z-10 size-full backdrop-blur" />
  <image src="/src/static/img/bg2.jpg" class="fixed left-0 top-0 -z-20 size-full" />
  <div class=" relative ml-[125rpx] mt-[100rpx] flex">
    <input v-model="keyword" type="text" class=" relative top-0 h-[70rpx] w-[430rpx] rounded-md bg-slate-200 pl-2 text-[26rpx] font-bold text-black opacity-75 shadow-inner shadow-[#888888]" placeholder="Please enter the Chinese" bindinput="inputChange" @confirm="filterData">
    <view class=" absolute left-[457rpx] top-0 h-[70rpx] w-[110rpx] rounded-lg bg-inherit" @tap="filterData">
      <div class=" size-full rounded-lg bg-slate-600 opacity-15" />
      <text class=" absolute left-[10px] top-[19rpx] text-[26rpx] font-semibold">
        Search
      </text>
    </view>
  </div>
  <scroll-view
    class=" absolute ml-[90rpx] mt-[50rpx] flex h-[900rpx] w-full flex-wrap" scroll-x="false" scroll-y="true"
  >
    <view
      v-for="(item, index) in filteredData"
      :key="index"
      class=" relative left-[20rpx] mt-[30rpx] h-[150rpx] w-[580rpx] rounded-[30rpx] border-none bg-inherit"
      @tap="hdlTap(index)"
    >
      <div class="absolute h-full w-[550rpx] rounded-[30rpx] bg-slate-700 opacity-45" />
      <div class=" absolute left-[20rpx] top-[15rpx] size-[120rpx] rounded-[30rpx] bg-gray-200 opacity-75">
        <text class=" flex items-center justify-center text-[90rpx]" selectable="false" space="false" decode="false">
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
