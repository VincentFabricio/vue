<script setup>
  const name = "Vue dinámico"
  const styleColor = "color: blue"
  const arrayColores = ["blue", "red", "peru"]
  const activo = true

  const objetoFruta = {
            name: "Manzana",
            price: "$1.00",
            description: "Una manzana",
  }

const arrayFrutas = [
    {
        name: "Manzana",
        price: "$1.00",
        description: "Una manzana",
        stock: 0,
    },
    {
        name: "Pera",
        price: "$2.00",
        description: "Una pera",
        stock: 10,
    },
    {
        name: "Naranja",
        price: "$3.00",
        description: "Una naranja",
        stock: 20,
    },
]

const handledClick = (messege) => {
  console.log(`Mensaje activación ${messege}`)
}

let counter=0

const increment = () => {
  console.log('Aumentar contador')
  counter++
}


</script>

<template>
  <div>
    <h1>
      Hola VUE JS {{ name.toUpperCase() }}
    </h1>
  </div>
  <h2 :style="`color: ${arrayColores[2]}`">{{ arrayColores }}</h2>
  <div>
    <h2 :style="styleColor">
      Soy Azul
    </h2>
  </div>
  <h2 v-if="activo === true"> Estoy activo </h2>
  <p v-else-if="activo === false">Estoy inactivo</p>
  <p v-else>Estoy indeciso</p>

  <h2 v-show="activo">Soy activo v-show</h2>
  {{ objetoFruta }}
  <ul>
    <li v-for="(value, propiedad, index) in objetoFruta" :key="value">
      {{ index }} - {{ propiedad }} : {{ value }}
    </li> 
  </ul>

  <ul>
    <template v-for="item in arrayFrutas" :key="item.name">
      <li v-if="item.stock > 0">
        {{ item.name }} - {{ item.price }}
      </li>
    </template>
    
  </ul>

  <button v-on:click.right.prevent="handledClick('Texto Right')">
    Activame 1
  </button>
  <button @click.left="handledClick('Texto Left')">
    Activame 2
  </button>
  <button @click.middle="handledClick('Texto Middle')">
    Activame 3
  </button>

  <div>
    <button @click="increment">Aumentar</button>
    <h2>{{ counter }}</h2>
  </div>


</template>



<style>
h1 {
  color: red;
}
</style>