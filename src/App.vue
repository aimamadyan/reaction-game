<template>
  <h1>Reaction Timer</h1>
  <h3 class="desc">Simple game by Imamadyan</h3>
  <button @click="start" :disabled="isPlaying">Play</button>
  <button @click="infos" :disabled="isPlaying">Info</button>
  <div v-if="showInfo">
    <p>Reaction timer app is a simple game based on VueJS. When you click play, it's going to wait a second or two until a green box appears. As soon as it appears, we have to click it as fast as we can. Then, the result will show up describing time and stage of our speed reaction.</p>
    <ol class="list">
      <li>Tap on play</li>
      <li>Tap ASAP when big green button shows</li>
      <li>Result how fast your finger is</li>
    </ol>
  </div>
  <Block v-if="isPlaying" :delay="delay" @end="endGame"/>
  <Result v-if="showResult" :score="score"/>
</template>

<script>
import Block from "@/components/Block.vue";
import Result from "@/components/Result.vue";
export default {
  name: 'App',
  components: {Result, Block },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResult: false,
      showInfo: false
    }
  },
  methods: {
    infos() {
      this.showInfo = !this.showInfo
      this.showResult = false
    },
    start() {
      this.isPlaying = true
      this.delay = 2000 + Math.random() * 5000
      this.showResult = false
    },
    endGame(reactionTime) {
      this.score = reactionTime
      this.isPlaying = false
      this.showResult = true
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
  color: #444;
  width: 100%;
  max-width: 68rem;
  margin: 0 auto;
}
@media screen and (min-width: 620px) {
  #app {
    font-size: 1.9rem;
    line-height: 1.31579;
  }
}
.list {
  list-style-position: inside;
}
.desc {
  color: #7c7c7c;
}
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
  cursor: not-allowed;
}
</style>
