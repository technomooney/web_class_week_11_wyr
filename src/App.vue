<template>
  <h1>Would you rather......</h1>

  <would-you-rather v-for="questionObject in wyrQuestionList"
                    v-bind:question="questionObject"
                    v-on:answer-changed="answerChanged"
                    v-bind:key="questionObject.id"
  ></would-you-rather>
  <h3>You would rather....</h3>
  <ul>
    <li v-for="message in filteredUserMessages">{{message}}</li>
  </ul>
</template>

<script>
import WouldYouRather from './components/WouldYouRather.vue'

export default {
  name: 'App',
  components: {
    WouldYouRather
  },
  data() {
    return {wyrQuestionList:[
        {wyrQuestion:"Would you rather be too hot or too cold?", wyrAnswer1:"Too hot", wyrAnswer2:"Too cold",id:0},
        {wyrQuestion:"Would you rather be able to make plants grow very quickly or be able to make it rain whenever you wanted?", wyrAnswer1:"Make plants grow very quickly", wyrAnswer2:"Make it rain whenever I wanted",id:1},
        {wyrQuestion:"Would you rather taste the best pizza that has ever existed once but never again or have the 4th best pizza restaurant in the world within delivery distance?", wyrAnswer1:"Taste the best pizza one time", wyrAnswer2:"Have4th best pizza place in delivery distance.",id:2},
        {wyrQuestion:"Would you rather own a restaurant or be a chef?", wyrAnswer1:"Make money but dont like cooking... I wouldn't mind just owning", wyrAnswer2:"Cook! let me be a chef!",id:3},
        {wyrQuestion:"Would you rather have a pet dinosaur of your choosing or a dragon the size of a dog?", wyrAnswer1:"Dino for meeeee!", wyrAnswer2:"Tiny dragon? Heck yea! I will just need to get a good insurance policy.",id:4},
        {wyrQuestion:"Would you rather be a scientist or be the boss of a company?", wyrAnswer1:"Scientist!", wyrAnswer2:"I'll own a company, like a boss!",id:5}
      ],
      userSelectedMessageList:[]
    }
  },
  methods: {
    answerChanged(choice,id) {
      this.userSelectedMessageList[id]=choice
    }
  },
  computed:{
    filteredUserMessages() {
      return this.userSelectedMessageList.filter(function (m) {
        if (m) {
          return m
        }
      })
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
  background-color: #00a0a0;
}
li {
  list-style: square;
  font-size: 30px;
}

</style>
