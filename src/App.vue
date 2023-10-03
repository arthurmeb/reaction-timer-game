<template>
  <div>  

    <h1>Reaction Timer Game</h1>
    <h3> Test your reaction speed!</h3>
    <button @click="startgame" :disabled="isPlaying">Play!</button>

  </div>

<div>   

  <Results v-if="gameEnded" :score="score"/>
  <Block v-if="isPlaying" :delay="delay" @endG="endGame"/>


</div>

</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',
  components: { Block, Results},
  data () {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      gameEnded: false
    }
  },
  methods: {
    startgame() {
      this.gameEnded = false
      this.isPlaying = !this.isPlaying
      this.timer()
      console.log(this.delay)    
    },
    timer() {
      this.delay = 1000 + Math.random() * 8000

    },
    endGame(reactionTime) {
      this.score = reactionTime
      this.isPlaying = !this.isPlaying
      console.log('Handled innit')
      this.gameEnded = true
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
</style>
