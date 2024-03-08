<script setup>
import { computed, ref } from 'vue'
const count = ref(0)
const doubleCount = computed(() => count.value * 2)
function increment() {
  count.value++
}
</script>

<template>
  <div>
    <h2>setupAttribute</h2>
    {{doubleCount}}
  </div>
  <el-button @click="increment">increment</el-button>
</template>
