<template>
  <div class="wyr">
    <h2>Would you rather.... </h2>

    <h3> {{ question.wyrQuestion }}</h3>

    <input v-bind:id="a1" name="radio1" type="radio"  v-bind:value="question.wyrAnswer1" v-model="choice" v-on:change="choiceMade">
    <label v-bind:for="a1" >{{question.wyrAnswer1}}</label>
    <input v-bind:id="a2" type="radio" v-bind:value="question.wyrAnswer2" v-model="choice" v-on:change="choiceMade">
    <label v-bind:for="a2">{{question.wyrAnswer2}}</label>
  </div>
</template>

<script>
export default {
  name: 'WouldYouRather',
  props: {question:Object
  },
  data() {
    return {
      choice:""
    }
  },
  methods: {
    choiceMade() {
      this.$emit("answer-changed", this.choice,this.question.id)
    }
  },
  computed: {
    a1() {
      return this.question.id
    },
    a2() {
      return this.question.id - (this.question.id * 2)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
.wyr {
  max-width: 75%;
  border: black 2px dashed;
  margin-left: auto;
  margin-right: auto;
  background: linear-gradient(darkseagreen,darkcyan);
}
</style>
