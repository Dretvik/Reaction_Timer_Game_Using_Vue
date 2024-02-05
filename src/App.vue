<template>
  <h1>Ellie's Reaction Timer</h1>
  <button class="startBtn" @click="startGame" :disabled="isPlaying">
    <p v-if="showResults">Play Again</p>
    <p v-else>Play</p>
  </button>

  <Block v-if="isPlaying" :delay="delay" @end="endGame"/>
  <Results v-if="showResults" :score="score"/>
</template>

<script>
import Block from './components/Block.vue';
import Results from './components/Results.vue';

export default {
  name: 'App',
  components: { Block, Results },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false,
    }
  },
  methods: {
    startGame() {
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      this.showResults = false;
    },
    endGame(reactionTime) {
      this.score = reactionTime;
      this.isPlaying = false;
      this.showResults = true;
    },
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: white;
  margin-top: 60px;
}
body {
  background: #2e2e2e;
  color: white;
}
.startBtn {
  background: #0faf87;
  color: white;
  border: none;
  padding: 14px 22px;
  border-radius: 10px;
  font-size: 26px;
  cursor: pointer;
  margin: 12px;
  box-shadow: 3px 3px 5px black;
}
.startBtn[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}

</style>
