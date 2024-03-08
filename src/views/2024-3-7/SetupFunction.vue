<script>
import { computed, ref } from 'vue'

export default {
  setup () {
    const count = ref(0)
    const doubleCount = computed(() => count.value * 2)

    function increment () {
      count.value++
    }
    return {
      count,
      doubleCount,
      increment
    }
  }
}

</script>

<template>
  <div>
    <h2>SetupFunction</h2>
    {{ doubleCount }}
  </div>
  <el-button @click="increment">increment</el-button>
</template>
