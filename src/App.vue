<template>
<h1>{{title}}</h1>
<p> Welcome to this new world</p>
<div v-if="showModal">
   <modal  theme="sale" @close="toggleModal">
     <h1>Hello,Welcome to VUE</h1>
     <p>This is the conent</p>
     <template v-slot:links>
       <a href="#"> Sign Up </a>
       <a href="#"> Learn more </a>
     </template>
   </modal>
</div>
<div v-if="showModal2">
   <modal  theme="sale" @close="toggleModal2">
     <h1>This is Modal Two</h1>
     <p>Learning vue is awesome</p>
     <template v-slot:sign >
       <a href="#"> Sign Up for the newsletter </a>
       <a href="#"> Learn more</a>
     </template>
   </modal>
</div>
<div >
  <button v-if="!showModal" @click="toggleModal">Show Modal One</button>
  <button v-if="!showModal2" @click="toggleModal2">Show Modal Two</button>
</div>
</template>
 
<script>

import Modal from '@/components/Modal'

export default {
  name: 'App',
  components: {
    modal: Modal
  },
  data() {
    return {
      title: 'Welcome',
      content: 'This is the content',
      showModal: false,
      showModal2:false,
      
    }
  },
  methods: {

    toggleModal:function(){
      this.showModal =! this.showModal
    },
    toggleModal2(){
      this.showModal2 = !this.showModal2
    }
  }
}
</script>

<style scoped>
  #modal, h1,p,div{
    margin: 20px auto;
    text-align: center;
  }
</style>
