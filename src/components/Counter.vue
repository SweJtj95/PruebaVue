<template>
  <h2> {{ customTitle }} </h2>
  <p> {{  counter  }} <sup> 2 </sup> = {{ squareCounter }}</p>

    <div>
        <button v-on:click="increase"> +1</button>
        <button v-on:click="decrease"> -1</button>

    </div>
  
</template>

<script>
export default {
    props: {
        title: String,
        start: {
            type: Number,
            required: true,

            validator(value){
                return value >100
            }


        },
    },
    //name: 'Patito'
    data () {
        return {
            counter: this.start
        }
    },
    methods: {
        squareCounter() {
            console.log("squareCounter");
            return  this.counter * this.counter
        },
        increase(){
             this.counter+=1;
        },
        decrease(){
             this.counter-=1;
        }

    },
     computed: {
    // Estas propiedades se guardan en  el cache
      squareCounter() {
        console.log("computed SquareCounter")
         return this.counter  * this.counter

      },

      customTitle(){
          return this.title || "Counter"
      }

  },

}
</script>

<style>

    button{
        
        background-color: aquamarine;
        border-radius: 5px;
        border: 1px solid white;
        color: white;
        cursor: pointer;
        margin: 0 5px;
        padding: 5px 15px;
        transition: 0.3s ease-in-out;
    }

    button:hover{
        background-color: #5aa67b;
        transition: 0.3s ease-in-out;

    }

</style>