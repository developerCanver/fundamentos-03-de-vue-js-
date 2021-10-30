<template>
  <h2>Counter !!</h2>
  <p>{{ counter }} <sup>2</sup> ={{ counter * counter  }}</p>
  <p>{{ counter }} <sup>2</sup> ={{ counter * counter  }}</p>
  <p>{{ counter }} <sup>2</sup> ={{ counter * counter  }}</p>

  <p>{{ counter }} <sup>2</sup> ={{ squareCounter  }}</p>
  <p>{{ counter }} <sup>2</sup> ={{ squareCounter  }}</p>
  <p>{{ counter }} <sup>2</sup> ={{ squareCounter  }}</p>
  <p>{{ counter }} <sup>2</sup> ={{ squareCounter  }}</p>
  <p>{{ counter }} <sup>2</sup> ={{ squareCounter  }}</p>
  <p>{{ counter }} <sup>2</sup> ={{ squareCounter  }}</p>


</template>

<script>

export default {
    data() {
        return{
            counter:5
        }
    },
    methods:{

        getSquareValue(){
            return 'Hola Mundo';
        }
    },
    computed:{
        //metodos compute se guardan en cahe
        //solo se ejecuta solo una vez 
        squareCounter(){
            console.log('squareCounter')
            return this.counter*this.counter;
        }
    }

}
</script>

<style>

</style>