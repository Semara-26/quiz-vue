<script setup>
import { ref, watch } from 'vue'
import data from '../data/quizes.json'

const quizzes = ref(data)

import quizCard from '../components/quizCard.vue'

const search = ref('')

watch(search, () => {
  quizzes.value = data.filter((quiz) => {
    return quiz.title.toLowerCase().includes(search.value.toLowerCase())
  })
})
</script>

<template>
  <header>
    <h1 id="title">Quizzes</h1>
    <input
      v-model.trim="search"
      type="text"
      id="search-input"
      placeholder="search here"
      autofocus
    />
  </header>
  <section id="quiz-container">
    <quizCard v-for="quiz in quizzes" :key="quiz.id" :quiz="quiz" />
  </section>
</template>

<style scoped>
header {
  margin-top: 20px;
  margin-bottom: 10px;
  display: flex;
  align-items: center;
}

#title {
  font-weight: bold;
  margin-right: 30px;
}

#search-input {
  border: none;
  border-radius: 5px;
  padding: 5px;
  background-color: #c9c9c9a6;
}

#quiz-container {
  display: flex;
  flex-wrap: wrap;
  margin-top: 20px;
  gap: 50px;
}
</style>
