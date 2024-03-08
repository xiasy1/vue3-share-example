<template>
  <div class="container">
    <Watermark text="众乐邦">
      <div class="content"></div>
    </Watermark>
    <Watermark text="版权所有" :font-size="20" :gap="15">
      <div class="content"></div>
    </Watermark>
  </div>
</template>

<script setup>
import Watermark from '@/views/2024-3-8/Watermark.vue'
</script>

<style scoped>
.container {
  padding: 100px 0;
  display: flex;
  justify-content: space-around;
}
.content {
  width: 600px;
  height: 650px;
  border: 1px solid silver;
}
</style>