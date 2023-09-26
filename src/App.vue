<template>
  <div>  
    <h1>Reaction Timer Game</h1>
    <h3> Test your reaction speed!</h3>
    <button @click="startgame" :disabled="isPlaying" >Play!</button>

</div>
<div>   
  <Block v-if="isPlaying" :delay="delay"/>
</div>
 
</template>

<script>
import Block from './components/Block.vue'

export default {
  name: 'App',
  components: { Block},
  data () {
    return {
      isPlaying: false,
      delay: null
    }
  },
  methods: {
    startgame() {
      this.isPlaying = !this.isPlaying
      this.timer()
      console.log(this.delay)    
    },
    timer() {
      this.delay = 1000 + Math.random() * 8000

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
