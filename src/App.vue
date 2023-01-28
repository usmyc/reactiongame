<template>
  <h1>Reaction Game</h1>
  <button @click="startGame" :disabled="isPlaying">Click</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame" />
  <Result v-if="showReaction" :reaction="reaction" />
</template>

<script>
import Block from "./components/Block.vue";
import Result from "./components/Result.vue";
export default {
  name: "App",
  components: { Block, Result },
  data() {
    return {
      isPlaying: false,
      showReaction: false,
      delay: null,
      reaction: 0,
    };
  },

  methods: {
    startGame() {
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      this.showReaction = false;
    },
    endGame(reactionTime) {
      this.reaction = reactionTime;
      this.isPlaying = false;
      this.showReaction = true;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}
</style>
