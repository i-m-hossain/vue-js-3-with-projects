<template>
  <div class="block" v-if="showBlock" @click='stopTimer'>
      
  </div>
</template>

<script>
export default {
    props:['delay'],
    data(){
      return{
          showBlock: false,
          reactionTime: 0,
          timer: null

      }
      
    },
   
    mounted() {
        setTimeout(() => {
            this.showBlock = true
            this.startTimer()
        }, this.delay);
    },
    methods:{
        startTimer(){
            this.timer = setInterval(() => {
                this.reactionTime +=10
            },10)
        },
        stopTimer(){
            clearInterval(this.timer)
            this.$emit('end', this.reactionTime)
            
        }
    }
}
</script>

<style>
    .block{
        width: 400px;
        margin: 20px auto;
        padding: 100px 0;
        background: #0faf87;
        color: #fff;
        text-align: center
    }
</style>