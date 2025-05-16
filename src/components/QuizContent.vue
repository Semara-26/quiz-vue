<template>
  <section id="question-container">
    <h3 class="question-title">{{ question.text }}</h3>
  </section>
  <section id="option-container">
    <div class="option" v-for="option in question.answers" :key="option.id">
      <p class="option-label">{{ option.label }}</p>
      <div class="option-value">{{ option.text }}</div>
    </div>
  </section>
</template>

<script setup>
import { defineProps } from 'vue';

const { question } = defineProps(['question'])
</script>

<style scoped>
#question-container {
  margin: 20px 0;
}

.question-title {
    font-size: 25px;
    font-weight: bold;
    margin-bottom: 20px;
}

#option-container {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.option {
  display: flex;
  align-items: center;
  gap: 10px;
  padding: 2px 10px;
  border: 1px solid #c9c9c9;
  border-radius: 8px;
  cursor: pointer;
  transition: all 0.3s ease;
  box-shadow: 0px 0px 5px 0px rgba(0, 0, 0, 0.75);
  -webkit-box-shadow: 0px 0px 5px 0px rgba(0, 0, 0, 0.75);
  -moz-box-shadow: 0px 0px 5px 0px rgba(0, 0, 0, 0.75);
}

.option:hover {
  background-color: #c9c9c9;
}

.option-label {
  font-size: 20px;
  font-weight: bold;
  background-color: #23b74b;
  color: #f6f6f6;
  padding: 5px 10px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center
}

.option-value {
  font-size: 18px;
  font-weight: bold;
}
</style>
