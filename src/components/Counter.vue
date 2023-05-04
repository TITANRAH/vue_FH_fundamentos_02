<template>
  <h2>{{ customTitle }}</h2>
  <p>{{ counter }} <sup>2</sup> = {{ squareCounter }}</p>

  <div>
    <button @click="increase()">+ 1</button>
    <button @click="decrease()">- 1</button>
  </div>
</template>

<script>
export default {
  // la diferencia entre properti y atributo es que las propertis
  // estan definidas aqui pero puedo escribir atrinutos en los compoenntes hijos y
  // al no estar definidas aca son atrinbutos
  props: {
    title: String,

    // puedo especificar aca la properti si es que no la envio en el componente hijo
    start: {
      type: Number,
      default: 100,
      validator(value) {
    if(value > 100){
        console.log('es mayor a 100')
    }else {
        console.log('no es mayor a 100 ')
    }
      },
    },
  },
  data() {
    return {
      counter: this.start,
    };
  },

  methods: {
    getSquareValue() {
      return this.counter * this.counter;
    },

    increase() {
      return this.counter++;
    },

    decrease() {
      return this.counter--;
    },
  },

  computed: {
    squareCounter() {
      return this.counter * this.counter;
    },

    // no es un metodo es una propiedad computada
    customTitle() {
      return this.title === "" ? "Counter" : this.title;
    },
  },
};
</script>

<style>
button {
  background-color: #64b687;
  border-radius: 5px;
  border: 1px solid white;
  color: white;
  cursor: pointer;
  margin: 0 5px;
  padding: 5px 15px;
  transition: 0.3s ease-in-out;
}

button:hover {
  background-color: #2f5540;
  transition: 0.3s ease-in-out;
}
</style>