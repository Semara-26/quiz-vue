<template>
  <main class="container">
    <RouterView />
  </main>
</template>

<script setup>
import { RouterView } from 'vue-router'
</script>

<style scoped>
main {
  max-width: 85%;
  margin: 0 auto;
}
</style>
