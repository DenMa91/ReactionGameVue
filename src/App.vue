<template>

<div class="container">
  <div class="row justify-content-center">
    <div class="col-12">
      <h1 class="display-1 px-5">Valuta i tuoi tempi di reazione</h1>
    </div>
    <div class="col-10">
      <p class="fs-5">clicca sul bottone, dopo un intervallo di tempo casuale apparirá un rettangolo verde, cliccaci sopra piu veloce che puoi e calcola la tua velocitá di reazione!!!</p>
  <button class="my-3 btn btn-success" @click="start" :disabled="isPlaying">play</button>
  <block v-if="isPlaying" :delay="delay" @end='endGame'/>
  <results v-if="showResults" :score='score'/>
    </div>
  </div>
</div>
  
</template>

<script>
import Block from './components/block.vue'
import results from './components/results.vue'

export default {
  name: 'App',
  components: { Block, results },
  data(){
    return{
      isPlaying:false,
      delay:null,
      score: null,
      showResults:false,
    }
  },
  methods:{
    start(){
      this.delay = 2000 + Math.random()*5000
      this.isPlaying = true
      this.showResults= false
    },
    endGame(reactionTime){
      this.score= reactionTime
      this.isPlaying= false
      this.showResults=true
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
  color: #333;
  margin-top: 60px;
}
</style>
