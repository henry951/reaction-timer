<template>
  <div>
    <h1>Reaction Timer</h1>
    <button @click="start" :disabled="isPlaying">Play</button>
    <Block :delay="delay" v-if="isPlaying" @end="endGame"/>
    <Results v-if="showResult" :score="score"/>
  </div>
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',
  components: {
    Block,
    Results
  },
  data(){
    return{
      isPlaying: false,
      delay: null,
      score: null,
      showResult: false,
    }
  },
  methods:{
    start() {
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true
      this.showResult = false
    },
    endGame(reationTime) {
      this.score = reationTime
      this.isPlaying = false
      this.showResult = true
    },
  }
}
</script>

<style scoped>
button {
  background: #0faf87;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}
button[disabled] {
  opacity: 0.2;
  cursor:not-allowed;
}
</style>