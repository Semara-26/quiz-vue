<template>
<section class="result">
    <p>You Got: </p>
    <h1>{{ numberOfRightAnswers }} / {{ quizQuestionsLength }}</h1>
    <div class="message">
        <p>{{ message() }}</p>
    </div>
    <div class="buttons">
        <button>
            <router-link id="home-button" to="/">Home</router-link>
        </button>
    </div>
    
</section>
</template>

<script setup>
import { defineProps } from 'vue';
const { numberOfRightAnswers, quizQuestionsLength } = defineProps(['numberOfRightAnswers', 'quizQuestionsLength'])

function message () {
    if (numberOfRightAnswers === quizQuestionsLength) {
        return 'Did u use AI to do this fucking quiz?'
    } else if (numberOfRightAnswers < quizQuestionsLength && numberOfRightAnswers > 0) {
        return 'HAH! YOU SUCK! Son of a bitch!'
    } else {
        return 'BRUHHH...'
    }
}

</script>

<style scoped>
.result {
    text-align: center;
    padding: 100px 0;
}
p {
    font-size: 25px;
    font-weight: bold;
}

h1 {
    font-size: 50px;
    font-weight: bold;
    margin: 20px 0;
}

.buttons {
    display: flex;
    justify-content: center;
    gap: 20px;
    margin-top: 20px;
}

button {
    padding: 10px 20px;
    border: none;
    border-radius: 10px;
    background-color: #23b41b;
    color: #fff;
    font-size: 20px;
    cursor: pointer;
}

#home-button {
    text-decoration: none;
    color: #fff;
}

</style>
