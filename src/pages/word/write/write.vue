<script lang="ts" setup>
import data from '@/main.json'

function hdlTap(index: number) {
  uni.navigateTo({
    url: `/pages/word/word?index=${index}`,

  })
}

const ctx = ref<UniNamespace.CanvasContext | null>()

function initCanvas() {
  ctx.value = uni.createCanvasContext('canvas')
  ctx.value.lineWidth = 4
  ctx.value.lineCap = 'round'
  ctx.value.lineJoin = 'round'
  ctx.value.strokeStyle = 'blue'
}

onReady(() => {
  initCanvas()
})

const points = ref<{ X: number, Y: number }[]>([])

function draw() {
  const point1 = points.value[0]
  const point2 = points.value[1]
  points.value.shift()
  ctx.value!.moveTo(point1.X, point1.Y)
  ctx.value!.lineTo(point2.X, point2.Y)
  ctx.value!.stroke()
  ctx.value!.draw(true)
}

function touchstart(e: TouchEvent) {
  const startX = e.changedTouches[0].x as number
  const startY = e.changedTouches[0].y as number
  const startPoint = { X: startX, Y: startY }
  points.value.push(startPoint)
  ctx.value!.beginPath()
}

function touchmove(e: TouchEvent) {
  const moveX = e.changedTouches[0].x as number
  const moveY = e.changedTouches[0].y as number
  const movePoint = { X: moveX, Y: moveY }
  points.value.push(movePoint) // 存点
  const len = points.value.length
  if (len >= 2) {
    draw() // 绘制路径
  }
}

function touchend() {
  points.value = []
}

function clear() {
  ctx.value!.clearRect(0, 0, 750, 750)
  ctx.value!.draw()
}
</script>

<template>
  <view class="relative min-h-[400rpx] w-[200rpx]">
    <image src="/src/static/img/1.png" class="absolute left-0 top-0 w-[200rpx]" mode="widthFix" />
    <canvas
      id="canvas"
      canvas-id="canvas"
      class="absolute left-0 top-0 h-full w-[200rpx]"
      disable-scroll
      @touchstart="touchstart"
      @touchmove="touchmove"
      @touchend="touchend"
    />
  </view>

  {{ points }}
  <button @tap="clear">
    reset
  </button>
  <button
    v-for="(item, index) in data"
    :key="index"
    @tap="hdlTap(index)"
  >
    {{ item.chinese }}
  </button>
</template>
