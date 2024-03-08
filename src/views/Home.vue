<script setup>
import { ref } from 'vue'

const list = ref([
  { title: 'setup语法糖与setup函数', link: '/2024-3-7', time: '2024-3-7' },
  { title: '防篡改的水印', link: '/2024-3-8', time: '2024-3-8' }
])
</script>

<template>
  <h1>前端分享案例：</h1>
  <div class="list">
    <div v-for="(item, index) in list" :key="item.link">
      <el-link type="primary" :href="item.link" :underline="false">
        <span>{{ index+1 }}. {{ item.title }}</span>
      </el-link>
    </div>
  </div>
</template>

<style scoped>
.list {
  .el-link {
    text-indent: 2em;
    font-size: 18px;
    margin-bottom: 10px;
  }
}
</style>