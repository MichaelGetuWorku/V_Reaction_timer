<template>
  <h1>Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame" />
  <Results :score="score" v-if="showResult" />
</template>

<script>
import Block from './components/Block.vue';
import Results from './components/Results.vue';
export default {
  components: { Block, Results },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResult: false,
    };
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000;
      // random of millisecond from 2000 up to 7000
      this.isPlaying = true;
      this.showResult = false;
    },
    endGame(reactionTime) {
      this.score = reactionTime;
      this.isPlaying = false;
      this.showResult = true;
    },
  },
};
</script>

<style>
#app {
  margin-top: 60px;
  color: #444;
  text-align: center;
  font-family: Inter, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto,
    Oxygen, Ubuntu, Cantarell, 'Fira Sans', 'Droid Sans', 'Helvetica Neue',
    sans-serif;
}
button{
  background:#0faf87;
  color: white;
  border:none;
  padding:8px 16px;
  border-radius:4px;
  font-size:16px;
  letter-spacing:1px;
  cursor:pointer;
  margin:10px;
}
  
button[disabled]{
  opacity:0.2;
  cursor:not-allowed;
}
</style>
