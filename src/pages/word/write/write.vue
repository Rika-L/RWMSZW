// @ts-nocheck
<script lang="ts" setup>
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

const strokeTotal = ref(0)
const wordIndex = ref(0)
const stroke = ref(1)

function next() {
  if (stroke.value < strokeTotal.value) {
    stroke.value += 1
  }
}

function touchend() {
  points.value = []
  next()
}

function clear() {
  ctx.value!.clearRect(0, 0, 400, 400)
  ctx.value!.draw()
  ctx.value!.lineWidth = 4
  ctx.value!.lineCap = 'round'
  ctx.value!.lineJoin = 'round'
  ctx.value!.strokeStyle = 'blue'
}

onLoad((options) => {
  wordIndex.value = options!.wordIndex as number
  strokeTotal.value = options!.stroke as number
})

function auto() {
  setInterval(() => {
    next()
  }, 1000)
}
</script>

<template>
  {{ strokeTotal }}
  <view class="mt-[30px] flex w-full justify-center">
    <view class="relative size-[400rpx]">
      <image :src="`/static/img/${stroke}.png`" class="absolute left-0 top-0 w-[400rpx]" mode="widthFix" />
      <canvas
        id="canvas"
        canvas-id="canvas"
        class="absolute left-0 top-0 h-full w-[400rpx]"
        disable-scroll
        @touchstart="touchstart"
        @touchmove="touchmove"
        @touchend="touchend"
      />
    </view>
  </view>
  <button @tap="auto">
    auto
  </button>
  <button @tap="clear">
    clear
  </button>
  <view>共{{ stroke }} 笔</view>
  <button @tap="next">
    下一笔
  </button>
</template>
