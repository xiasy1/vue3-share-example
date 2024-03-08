<script setup>
import SetupAttribute from '@/views/2024-3-7/SetupAttribute.vue'
import SetupFunction from '@/views/2024-3-7/SetupFunction.vue'
import { onMounted, ref } from 'vue'

const setupAttributeRef = ref(null)
const setupFunctionRef = ref(null)

onMounted(() => {
  console.log('setupAttributeRef:', setupAttributeRef.value)
  console.log('setupFunctionRef:', setupFunctionRef.value)
})
</script>

<template>
  <setup-attribute ref="setupAttributeRef" />
  <setup-function ref="setupFunctionRef" />
</template>
