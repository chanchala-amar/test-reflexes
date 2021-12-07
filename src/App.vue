<template>
  <h2>How fast are you? Test your reflexes</h2>
  <button
    name="start"
    @click="startPlay"
    :class="{ deactivate: currentlyPlaying }"
  >
    Start Game
  </button>
  <game-block
    :delay="delayTime"
    v-if="currentlyPlaying"
    @endgame="showResult"
  />
  <result-block v-if="result" :time="result" />
</template>

<script>
import GameBlock from "./components/GameBlock.vue";
import ResultBlock from "./components/ResultBlock.vue";

export default {
  name: "App",
  components: {
    GameBlock,
    ResultBlock,
  },
  data() {
    return {
      currentlyPlaying: false,
      delayTime: 0,
      result: null,
      //gameTime: null,
    };
  },
  methods: {
    startPlay() {
      this.result = null;
      this.delayTime = 2000 + Math.random() * 5000;
      this.currentlyPlaying = true;
    },
    showResult(time) {
      this.result = time;
      this.currentlyPlaying = false;
      this.delayTime = null;
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
  color: #2c3e50;
  margin-top: 60px;
}
button {
  background: rgb(1, 109, 109);
  color: white;
  border: none;
  padding: 10px;
  border-radius: 5px;
  font-size: 15px;
  font-weight: bold;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}
.deactivate {
  opacity: 0.4;
  cursor: none;
}
</style>
