<template>
  <QuizHeader :questionPage="questionPage" />
  <QuizContent :question="quiz.questions[currentQuestionIndex]" />
  <button
    @click="currentQuestionIndex++"
    :disabled="currentQuestionIndex === quiz.questions.length - 1"
  >
    Next
  </button>
</template>

<script setup>
import QuizHeader from '@/components/QuizHeader.vue'
import QuizContent from '@/components/QuizContent.vue'
import { useRoute } from 'vue-router'
import { parse } from 'vue/compiler-sfc'
import quizes from '../data/quizes.json'
import { ref, computed, watch } from 'vue'

const route = useRoute()
const quizId = parseInt(route.params.id)
const quiz = quizes.find((quiz) => quiz.id === quizId)
const currentQuestionIndex = ref(0)
const questionPage = computed(() => `${currentQuestionIndex.value + 1} / ${quiz.questions.length}`)

// const questionPage = ref(`${currentQuestionIndex.value + 1} / ${quiz.questions.length}`)

// watch(
//   () => currentQuestionIndex.value,
//   () => (questionPage.value = `${currentQuestionIndex.value + 1} / ${quiz.questions.length}`),
// )
</script>

<style scoped></style>
