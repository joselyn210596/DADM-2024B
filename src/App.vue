<script setup>
import { ref } from 'vue';
// Modelo
const header = ref('App lista de compras');
//---items---
//items model
const items = ref([
  {id:'0', label: '10 bolillos', purchased: false, priority: true},
  {id:'1', label: '1 crema de litro', purchased: true, priority: true},
  {id:'2', label: '1/4 de jamon' , purchased: false, priority: false},
  {id:'3', label: '1 nutella' , purchased: true, priority: true}
]);
//item-metodo
const seveItem = () => {
  //accediendo a la variable reactiva items value.
  items.value.push({id:items.value.length + 1, label: newItem.value});
  //limpia el imput 
  newItem.value='';
};
//---formulario--
const newItem = ref('');
const newItemHighPriority = ref(false);
const editing = ref(true);
const activateEdition = (activate)=>{
  editing.value=activate;
};
// Alternando estado de compra del item
const togglePurchased = (item) => {
  item.purchased = !item.purchased;
};
//metodos 
</script>

<template>
  
<div class="header">
  <h1>
   <i class="material-icons shopping-cart-icon">local_mall</i> 
    {{ header }} 
  </h1>
  <button
   v-if="editing" 
   class="btn"
    @click="activateEdition(false)">
    Cancelar
  </button>
  <button
   v-else
    class="btn btn-primary" 
    @click="activateEdition(true)">
    Agregar Articulo
  </button>
  </div>

  <!---colocando un iperenlace-->
   <!---para poder poner link enla caja de texto v-bind:href="newItem"-->
     <!--para que cuando este bacia la caja de texto tenga un link
     :href="newItem === '' ? 'https://www.google.com' : 'https://' + newItem" 
    target="_blank" -->
 

  <!--- agrupando entradas de usuario-->
  <form 
  class="add-item form"
  v-if="editing"
   v-on:submit.prevent="seveItem">
  <input v-model="newItem" type="text" placeholder="Agregar un articulo" />
  <!--Caja de seleccion de Prioridad-->
  <label>
    <input type="checkbox" v-model="newItemHighPriority" />
    Alta Prioridad
  </label>
  <!--Boton-->
  <button 
  :disabled="newItem.length == 0"
  class="btn btn-primary">
    Salvar Articulo
  </button>
  </form>
  <ul></ul>

  {{ iceCreamFlavors }}
  <ul></ul>
  {{ newItemHighPriority }}
  <!-- Lista -->
  <ul>
    <li
      v-for="({ id, label, purchased, priority }, index) in items"
      @click="togglePurchased(items[index])"
      v-bind:key="id"
      :class="{ strikeout: purchased, priority: highPriority }"
    >
      ⚜ {{ label }}
    </li>
  </ul>
  <!-- Lista clases como objetos -->
  <ul>
    <li 
    v-for="{label,id, purchased, priority} in items" 
    :key="id" 
    class="amazing"
    :class="{ strikeout: purchased, priority:priority}"> 
    {{ priority ? "🔥": "👜" }} {{  label }} 
  </li>
  </ul>

  <!-- Lista clases como arreglos -->
  <ul>
  <li 
	v-for="({ id, label, purchased, highPriority }, index) in reversedItems"
  :class="{ strikeout: item.purchased, priority: item.priority }"
	@click="togglePurchased(reversedItems[index])" 
  v-bind:key="id">
	  ➡️ {{ label }}
</li>
  </ul>
  <p v-if="items.length === 0">🥀NO HAY ELEMENTOS EN LISTA🥀 </p>
</template>

<style scoped>
.shopping-cart-icon{
  font-size: 2rem;
}
</style>