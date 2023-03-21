<template>
  <div id="app">

    <h1>Would You Rather?</h1>

 
  <!-- breaks down and sends portions of the question object -->
    <would-you-rather 
    v-for="eachQuestion in questions" v-bind:key="eachQuestion.id"
    v-bind:question="eachQuestion"
    v-bind:answer1="eachQuestion.answer1"
    v-bind:answer2="eachQuestion.answer2"
    v-bind:id="eachQuestion.id"
    v-on:answer-changed="answerChanged"
    ></would-you-rather>
    
    
    <ul>
      <li v-for="answer in answerList" v-bind:key="answer">{{answer}}</li>
    </ul>
  </div>
</template>

<script>
import WouldYouRather from './components/WouldYouRather.vue'

export default {
  name: 'App',
  components: {
    WouldYouRather
  },
  data() {
    return {
      questions: [
        {
          id: 0,
          question:'Have a cat or have a dog?',
          answer1: 'Have a dog',
          answer2: 'Have a cat'
        },
        {
          id: 1,
          question: 'Be a Jedi or be a Sith?',
          answer1: 'Be a Jedi',
          answer2: 'Be a Sith'
        },
        {
          id: 2,
          question: 'Be an incredibly fast swimmer or an incredibly fast runner',
          answer1: 'Be an incredibly fast swimmer',
          answer2: 'Be an incredibly fast runner'
        }
      ],
      answerList: [null, null, null]  // null list to be filled with choices as they're made
    }
  },
  methods: {
    answerChanged(choice, id) {
        this.answerList[id] = choice
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

body {
  background: white;
}
</style>
