<template>
  <div class="watermark-container" ref="parentRef">
    <slot></slot>
  </div>
</template>

<script setup>
import { ref ,onMounted, onUnmounted } from 'vue'
import useWatermarkBg from '@/views/2024-3-8/useWatermarkBg.js'

const parentRef = ref(null)
const props = defineProps({
  text: {
    type: String,
    required: true,
    default: 'watermark'
  },
  fontSize: {
    type: Number,
    default: 40
  },
  gap: {
    type: Number,
    default: 20
  }
})
const bg = useWatermarkBg(props)

let div
function resetWatermark () {
  if (!parentRef.value) return
  const { base64, size } = bg.value
  div = document.createElement('div')
  div.style.position = 'absolute'
  div.style.backgroundImage = `url(${base64})`
  div.style.backgroundSize = `${size}px ${size}px`
  div.style.backgroundRepeat = 'repeat'
  div.style.zIndex = '9000'
  div.style.inset = '0'
  // div.style.pointerEvents = 'none'
  parentRef.value.appendChild(div)
}

const ob = new MutationObserver((entries) => {
  console.log('DOM变化：', entries)
  for (const entry of entries) {
    for (const node of entry.removedNodes) {
      node === div && resetWatermark()
    }
    if (entry.target === div) {
      div.remove()
      resetWatermark()
    }
  }
})

onMounted(() => {
  resetWatermark()
  ob.observe(parentRef.value, {
    childList: true,
    subtree: true,
    attributes: true
  })
})
onUnmounted(() => ob.disconnect())
</script>

<style scoped>
.watermark-container {
  position: relative;
}
</style>