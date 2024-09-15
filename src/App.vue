<template>
  <h1>Reaction Timer</h1>
  <p>Click the button below to start the game</p>
  <button class="play-btn" @click="start" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame" />
  <Result v-if="showResults" :score="score" />
  <!-- <p class="results" v-if="showResults">Your Reaction Time: {{ score }} ms</p> -->
</template>

<script>
import Block from "./components/Block.vue";
import Result from "./components/Result.vue";

export default {
  name: "App",
  components: {
    Block,
    Result,
  },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false,
    };
  },
  methods: {
    start() {
      this.isPlaying = true;
      this.delay = 2000 + Math.random() * 5000;
      this.showResults = false;
    },
    endGame(reactionTime) {
      this.score = reactionTime;
      this.isPlaying = false;
      this.showResults = true;
    },
  },
};
</script>

<style>
#app {
  text-align: center;
}
.play-btn {
  font-size: 1.5rem;
  color: #fff;
  background-color: #000;
  border: none;
  border-radius: 2rem;
  padding: 1rem 4rem;
  margin-top: 2rem;
  cursor: pointer;
  transition: all 0.3s ease;
}
.play-btn:hover {
  background-color: #fff;
  color: #000;
  border: 1px solid #000;
}
.results {
  font-size: 1.5rem;
  margin-top: 2rem;
}
</style>
