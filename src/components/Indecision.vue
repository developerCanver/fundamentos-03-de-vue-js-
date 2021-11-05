<template>
<img v-if="img" :src="img" alt="bg">
<div class="bg-dark">

</div>

<div class="indecision-container">
    <input type="text" v-model="question" placeholder="realiza una pregunta">
    <p>Recuerda terminar con un signo de Interrogación</p>

    <div v-if="isValiQuestion"> 

    <h2>{{question}}</h2>
    <h1>{{answer}}</h1>
    </div>
</div>
</template>

<script>
import { watch } from "@vue/runtime-core";

export default {

data(){
    return{
        question:'',
        answer: null,
        img:'',
        isValiQuestion : false,

    }
},
watch:{
// es para mitigar si hay cambios
 question(value, oldValue){ 
     //tiene que llamarse igual que la propiedad que se asigno
     this.isValiQuestion=false
 
    if (!value.includes('?')) return

    this.isValiQuestion=true
    this.getAnswer()

    },
},
methods:{
  async getAnswer(){
      this.answer='Pensando..'

      const  resp  = await fetch('https://yesno.wtf/api').then( r=> r.json())
     
      this.img=resp.image
      this.answer= resp.answer === 'yes' ? 'SI!' : ' NO' 


  }
}
}
</script>

<style >

    img, .bg-dark {
        height: 100vh;
        left: 0px;
        max-height: 100%;
        max-width: 100%;
        position: fixed;
        top: 0px;
        width: 100vw;
    }

    .bg-dark {
        background-color: rgba(0, 0, 0, 0.4);
    }

    .indecision-container {
        position: relative;
        z-index: 99;
    }
    
    input {
        width: 250px;
        padding: 10px 15px;
        border-radius: 5px;
        border: none;
    }
    input:focus {
        outline: none;
    }

    p {
        color: white;
        font-size: 20px;
        margin-top: 0px;
    }

    h1, h2 {
        color: white;
    }
    
    h2 {
        margin-top: 150px;
    }

</style>