<template>
  <header>
    <h1 id="title">Questions {{ questionPage }}</h1>
    <div class="bar">
      <div class="bar-progress" :style="{ width: pagePercent }"></div>
    </div>
  </header>
</template>

<script setup>
import { defineProps } from 'vue'

const { questionPage, pagePercent } = defineProps(['questionPage', 'pagePercent'])
</script>

<style scoped>
header {
  margin-top: 20px;
}

#title {
  font-size: 30px;
  font-weight: bold;
}

.bar {
  width: 100%;
  height: 30px;
  border: 3px solid #23b41b;
  border-radius: 50px;
  overflow: hidden;
}

.bar-progress {
  width: 0%;
  height: 100%;
  background-color: #23b41b;
}
</style>
