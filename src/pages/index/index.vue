<script lang="ts" setup>
import data from '@/main.json'

function hdlTap(index: number) {
  uni.navigateTo({
    url: `/pages/word/word?index=${index}`,

  })
}
</script>

<template>
  <button
    v-for="(item, index) in data"
    :key="index"
    @tap="hdlTap(index)"
  >
    {{ item.chinese }}
  </button>
</template>
