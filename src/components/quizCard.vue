<script setup>
import { defineProps } from 'vue';
import { useRouter } from 'vue-router';

const router = useRouter()
const { quiz } = defineProps(['quiz'])

function goToQuiz() {
  router.push({
    name: 'quiz',
    params: {
      id: quiz.id
    }
  })
}
</script>

<template>
  <div class="card" @click="goToQuiz">
    <img :src="quiz.img" alt="quiz.title" />
    <div class="card-body">
      <h2>{{ quiz.title }}</h2>
      <p>{{ quiz.questions.length }} Questions</p>
    </div>
  </div>
</template>

<style scoped>
.card {
  width: 270px;
  /* border: 1px solid #c9c9c9; */
  border-radius: 8px;
  overflow: hidden;
  cursor: pointer;
  transition: all 0.3s ease;
  box-shadow: 0px 0px 5px 0px rgba(0, 0, 0, 0.75);
  -webkit-box-shadow: 0px 0px 5px 0px rgba(0, 0, 0, 0.75);
  -moz-box-shadow: 0px 0px 5px 0px rgba(0, 0, 0, 0.75);
  margin-top: 30px;
}

.card img {
  width: 100%;
  height: 200px;
  object-fit: cover;
  transition: all 0.3s ease;
  margin: 0;
}

.card-body {
  padding: 10px;
}

.card-body h2 {
  margin: 0;
  font-weight: bold;
}

.card:hover {
  transform: scale(1.05);
  box-shadow: 0px 0px 10px 0px rgba(0, 0, 0, 0.75);
  -webkit-box-shadow: 0px 0px 10px 0px rgba(0, 0, 0, 0.75);
  -moz-box-shadow: 0px 0px 10px 0px rgba(0, 0, 0, 0.75);
}
</style>
