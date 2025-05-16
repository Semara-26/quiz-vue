<template>
  <QuizHeader :questionPage="questionPage" :pagePercent="pagePercent" />
  <QuizContent
    v-if="!showResult"
    :question="quiz.questions[currentQuestionIndex]"
    @selectOption="onSelectOption"
  />
  <QuizResult
    v-else
    :quizQuestionsLength="quiz.questions.length"
    :numberOfRightAnswers="numberOfRightAnswers"
  />
</template>

<script setup>
import QuizHeader from '@/components/QuizHeader.vue'
import QuizContent from '@/components/QuizContent.vue'
import QuizResult from '@/components/QuizResult.vue'
import { useRoute } from 'vue-router'
import { parse } from 'vue/compiler-sfc'
import quizes from '../data/quizes.json'
import { ref, computed } from 'vue'

const route = useRoute()
const quizId = parseInt(route.params.id)
const quiz = quizes.find((quiz) => quiz.id === quizId)
const currentQuestionIndex = ref(0)
const numberOfRightAnswers = ref(0)
const showResult = ref(false)

const questionPage = computed(() => `${currentQuestionIndex.value + 1} / ${quiz.questions.length}`)

const pagePercent = computed(
  () => `${((currentQuestionIndex.value + 1) / quiz.questions.length) * 100}%`,
)

function onSelectOption(option) {
  if (option.correct) {
    numberOfRightAnswers.value++
  }

  if (quiz.questions.length - 1 === currentQuestionIndex.value) {
    showResult.value = true
    return
  }

  currentQuestionIndex.value++
}

// const questionPage = ref(`${currentQuestionIndex.value + 1} / ${quiz.questions.length}`)

// watch(
//   () => currentQuestionIndex.value,
//   () => (questionPage.value = `${currentQuestionIndex.value + 1} / ${quiz.questions.length}`),
// )
</script>

<style scoped></style>
