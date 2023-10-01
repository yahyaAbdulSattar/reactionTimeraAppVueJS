<template>
  <body>
    <h1>Ninja Reaction Timer</h1>
    <button @click="start" :disabled="isPlaying">play</button>
      <Block v-if="isPlaying" :delay="delay" @end="endGame"/>
      <Result v-if="showResults" :score="score"/>
        
      
  </body>
  
</template>

<script>
  import Block from './components/Block.vue'
  import Result from './components/Results.vue'
  export default {
    name: 'App',
    components: { Block, Result },
    data(){
      return{
        isPlaying: false,
        delay: null,
        score: null,
        showResults: false
        
      }
    },
    methods: {
      start(){
        this.delay = 2000 + Math.random() * 5000,
        this.isPlaying = !this.isPlaying
        this.showResults = false
      },
      endGame(reactionTime){
        this.score = reactionTime
        this.isPlaying = false
        this.showResults = true
      }
    }
  }
</script>
<style scoped>
  body{
    text-align: center;
  }
  
  
</style>
