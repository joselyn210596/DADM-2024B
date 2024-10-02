<script setup>
import { ref } from 'vue';
// Modelo
const header = ref('App lista de compras');
//-----items-------
// item-Model
const items = ref([
  {id:'0', label: '10 bolillos'},
  {id:'1', label: '1 crema de cuerpo'},
  {id:'2', label: '1 chela'},
  {id:'3', label: '1 nutella'}
]);
//Item-Method
const saveItem = () =>{
  // Add new item
  items.value.push({id:items.value.length+ 1, label: newItem.value});
  // limpia el input
  newItem.value='';
};
const newItem = ref("");
const newItemHighPriority = ref(false);

//Metodos
</script>

<template>
  <h1>
   <i class="material-icons shopping-cart-icon">local_mall</i> 
    {{ header }} 
  </h1>
  <form class="add-item form" v-on:submit.prevent="saveItem()">
  <input v-model="newItem" type="text" placeholder="Agregar un articulo" />
  <!--Caja de seleccion de Prioridad-->
  <label>
    <input type="checkbox" v-model="newItemHighPriority" />
    Alta Prioridad
  </label>
  <!--Boton-->
  <button class="btn btn-primary">
    Salvar Articulo
  </button>
  </form>
  <ul></ul>
 
  {{ iceCreamFlavors }}
  <ul></ul>
  {{ newItemHighPriority }}
  <!-- Lista -->
  <ul>
    <li v-for="item in items" :key="item.id"> 👝 {{  item.label }} </li>
  </ul>
</template>

<style scoped>
.shopping-cart-icon{
  font-size: 2rem;
}
</style>