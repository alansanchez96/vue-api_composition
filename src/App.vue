<script setup>

import { computed, ref } from "vue";

const btnActive = message => console.log(message);

const counter = ref(0); // Se le indica que es una variable reactiva
const increment = () => counter.value++; // Se le debe agregar value

/* Ejercicio 1*/
const counterEjercicio = ref(0);
const numbers = ref([1, 2, 3]);
let activador = ref(false);

const incrementarEjercicio = () => {
  counterEjercicio.value++;
  evaluarCounter();
}
const decrementarEjercicio = () => {
  counterEjercicio.value--;
  evaluarCounter();  
}
const resetEjercicio = () => {
  counterEjercicio.value = 0;
  evaluarCounter();
}
const classComputed = computed(() => {
  if (counterEjercicio.value === 0) {
    return 'neutral';
  } else if (counterEjercicio.value > 0) {
    return 'positivo';
  } else {
    return 'negativo';
  }
});

const agregarNumero = counter => {
  if (numbers.value.includes(counter)) {
    activador.value = true;
  } else {
    numbers.value.push(counter);
    activador.value = true;
  }
}

const evaluarCounter = () => {
  if (numbers.value.includes(counterEjercicio.value)) {
    activador.value = true;
  } else {
    activador.value = false;
  }
}

</script>

<template>

  <h1>Reactividad</h1>

  <h3>Eventos</h3>

  <button @click.left="btnActive('diste click con izquierdo')">Activame con click izquierdo</button>
  <button @click.middle="btnActive('diste click con scroll')">Activame con click scroll</button>
  <button @click.right.prevent="btnActive('diste click con derecho')">Activame con click derecho</button>

  <hr>

  <h3>Contador {{ counter }}</h3>
  <!-- Se debe importar la libreria "ref" -->

  <button @click="increment">Activar contador</button>

  <hr>

  <h3>Ejercicio</h3>

  <p>Contador <span :class="classComputed"> {{ counterEjercicio }}</span></p>

  <button @click="incrementarEjercicio">Incrementar</button>
  <button @click="decrementarEjercicio">Decrementar</button>
  <button @click="resetEjercicio">reset</button>
  <button @click="agregarNumero(counterEjercicio)" :disabled="activador">Agregar</button> <br>

  <ul>
    <li v-for="number in numbers">{{ number }}</li>
  </ul>

</template>

<style>
.positivo {
  color: green;
}

.negativo {
  color: red;
}

.neutral {
  color: blue;
}
</style>