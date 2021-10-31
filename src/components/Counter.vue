<template>
  <h2>{{ customTitle }} !!</h2>
  <p>{{ counter }} <sup>2</sup> ={{ counter * counter  }}</p> 
 


<div>
    <button @click="inicrease()">+1</button>
    <button @click="decrease()">-1</button>
</div>

</template>

<script>

export default {
    props: {
        title: String,
        start: {
            type: Number,
            default: 0,
            validate(value){
                return value >= 100
            }
        },
    },

    data() {
        return{
            counter:0,
        }
    },
    methods:{

        getSquareValue(){
            return 'Hola Mundo';
        },
        inicrease(){
            this.counter++;
        },
        decrease(){
            this.counter--;
        },
    

        
    },
    computed:{
        //metodos compute se guardan en cahe
        //solo se ejecuta solo una vez 
        squareCounter(){
            console.log('squareCounter')
            return this.counter*this.counter;
        },
            customTitle(){
           // return this.title || 'Counter'
            return this.title ?  this.counter : 'Couneter'
        }
    }

}
</script>

<style>
.button{
    background-color: #64b687;
    border-radius: 5px;
    border: 1px solid #ffffff;
    color:#ffffff;
    cursor:pointer;
    padding: 5px 15px;
    transition: 0.3s ease-in-out;
    margin: 0 5px;
}

button:hover{
    background-color: #5aa67b;
    transition: 0.3s ease-in-out;
}
</style>