<template>

  
  <div id="play">
      <h2>Ninja Reaction Timer</h2>
      <button @click="start" :disabled="isPlaying">play</button>
  </div>
  
    <Block v-if="isPlaying" :delay="delay" @end="endGame"/>

    <Results v-if="showResults" :score="score" />

</template>
 
<script>

import Block from '@/components/Block'
import Results from '@/components/Results'

export default {
  

  components:{
    Block, Results
  },
  data(){
    return{
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false  
    }
  },
  methods:{
    start(){
      this.delay = 2000 + Math.random() * 5000 
      this.isPlaying = true
      this.showResults=false

    },
    endGame(reactionTime){
      this.score = reactionTime
      this.isPlaying =false
      this.showResults=true
      
    }
    
  }
}
</script>

<style>


  #app{
    font-family: Avenir, Helvetica, Arial;
    text-align: center;
    margin-top:60px;
    color: #444;
  }
  
 
   button{
    color:#fff;
    background: #0faf87;
    padding:8px 16px;
    border-radius:4px;
    font-size: 16px;
    letter-spacing:1px;
    cursor: pointer;
    border: none;
    margin: 10px;
  } 
  button[disabled]{
    cursor: not-allowed;
    opacity: .2;

  }

</style>
