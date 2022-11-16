<script setup>

const parrafoStyle = 'color:red';
const arrayColor = ['azul', 'violet', 'orange'];
const active = true;
const frutas = ['banana', 'pera', 'manzana', 'anana'];

const arrObjFrutas = [
  {
    name: "Manzana",
    price: "$1.00",
    description: "Una manzana",
    id: 1
  },
  {
    name: "Pera",
    price: "$2.00",
    description: "Una pera",
    id: 2
  }
];

const objFrutas = {
  id: 1,
  name: 'Banana',
  price: '$1,00',
  description: 'Una banana',
  stock: 15
}

</script>

<template>

  <h3>V-BIND</h3>
  <p :style="parrafoStyle">Soy un texto prueba de bind</p>
  <p :style="`color: ${arrayColor[1]}`">Mis colores provienen de un array</p>

  <hr>

  <h3>DIRECTIVAS V-IF</h3>

  <p v-if="active === true">Estoy activo</p>
  <p v-else-if="active === false">Estoy inactivo</p>
  <p v-else>Estoy indeciso</p> <!-- null -->
  <!-- Tambien se pueden usar los operadores ternarios -->
  <p>{{ active ? 'Está activo' : 'Esta inactivo' }}</p>

  <h3>V-SHOW</h3>

  <p v-show="active">Solo aparece y desaparece con un display:none. Para ver la accion, cambie el active por "false"</p>
  <!-- 
        En terminos generales "v-if" tiene costos  más altos que "v-show".
        En v-show es mejor utilizarlo cuando quieres que un cambio se realice con mucha frecuencia
        Y v-if cuando el cambio no sea tan necesario
       -->

  <hr>

  <h3>V-FOR</h3>

  <ul>
    <li v-for="(fruta, index) in frutas">{{ index }} - {{ fruta }}</li>
  </ul>

  <h3>V-FOR CON ARRAY DE OBJETOS</h3>

  <ul>
    <li v-for="(fruta, index) in arrObjFrutas" :key="fruta.id">
      <p>{{ index }} - {{ fruta.name }}</p>
      <p>Precio: {{ fruta.price }}</p>
      <p>Descripcion: {{ fruta.description }}</p>
    </li>
  </ul>

  <h3>V-FOR CON OBJETOS</h3>

  <ul>
    <li v-for="(value, property, index) in objFrutas">
      {{ property }} : {{ value }}
    </li>
  </ul>

  <h3>V-FOR CON V-IF</h3>
  <!-- La manera correcta es la siguiente -->

  <ul>
    <template v-for="(fruta) in objFrutas">
      <li v-if="fruta.stock > 0">{{ fruta.name }}</li>
    </template>
  </ul>


  
</template>