<template>
  <div class="wyr">
    <h2>Please make your choice.... </h2>

    <h3> {{ question }}</h3>

    <input type="radio" id="a1" v-bind:value="answer1" v-model="choice" v-on:change="choiceMade">
    <label for="a1">{{answer1}}</label>
    <input type="radio" id="a2" v-bind:value="answer2" v-model="choice" v-on:change="choiceMade">
    <label for="a2">{{answer2}}</label>
  </div>
</template>

<script>
export default {
  name: 'WouldYouRather',
  props: {
    question:String,
    answer1:String,
    answer2:String
  },
  data() {
    return {
      choice:""
    }
  },
  methods: {
    choiceMade() {
      this.$emit("answer-changed", this.choice)
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
  border: black 2px dashed;

}
</style>
