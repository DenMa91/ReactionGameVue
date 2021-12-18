<template>
  <p>Reaction time: {{score}}ms </p>
  <p class="rank">{{rank}}</p>
</template>

<script>
export default {
 props:['score'],
 data(){
     return{
         rank:null
     }
 },
 mounted(){
     if(this.score < 270){
         this.rank = 'ottimi riflessi'
     }else if(this.score < 450){
         this.rank = 'buoni riflessi'
     }else{this.rank = 'devi allenarti'}
 }
}
</script>

<style>
.rank{
    color: black;
    font-weight: bold;
    font-size: 20px;
}
</style>