<template>
  <div class="wyr">

  <h2>Would you rather...</h2>

    <h3>...{{ question.question }}</h3>
    <input type="radio" v-model="choice" v-bind:value="question.answer1" v-on:change="choiceMade"><label>{{question.answer1}}</label>
    <input type="radio" v-model="choice" v-bind:value="question.answer2" v-on:change="choiceMade"><label>{{question.answer2}}</label>

  </div>
</template>

<script>
export default {
  name: 'WouldYouRather',
  emits: ['answer-changed'],  // this might be useless
  props: {
    question: Object
  },
  data() {
    return {
      choice: ''
    }
  },
  methods: {
    choiceMade() {  // emits the choice and object's id back to the parent component
      this.$emit('answer-changed', this.choice, this.question.id)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.wyr {
  text-align: left;
  background-color: rgb(243, 52, 52);
  color: black;
}

h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
