<template>
  <h1>Would you rather......</h1>

  <would-you-rather v-bind:question="wyrQuestion"
  v-bind:answer1="wyrAnswer1"
  v-bind:answer2="wyrAnswer2"
  v-on:answer-changed="answerChanged"
  ></would-you-rather>

  <p> {{userSelectedMessage}}</p>
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
      wyrQuestion:"Would you rather be too hot or too cold?",
      wyrAnswer1:"Too hot",
      wyrAnswer2:"Too cold",
      userSelectedMessage:""
    }
  },
  methods: {
    answerChanged(choice) {
      this.userSelectedMessage = `Thanks you selected \"${choice}\"`
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
</style>
