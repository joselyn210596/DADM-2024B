<script setup>
import{ref} from 'vue';
const header = ref('App lista de compras');
const items = ref([
    {id:'0', label: '10 bolillos'},
    {id:'1', label: '1 lata de frijoles'},
    {id:'2', label: '1 nutella'},
    {id:'3', label: '1 chela'}
    
]);
const newItem =ref('');
const newItemPriority= ref('low');
</script>

<template>
<h1> 
    <i class="material-icons shopping-cart-icon">local_mall </i>
    {{ header }}
</h1>
<input v-model="newItem" type="text"placeholder="Agregar Articulo">
<!-- RADIO BUTTOS-->
 <label>
    <input type="radio" value="low" v-model="newItemPriority">
    Bajo
</label>
 <label>
    <input type="radio" value="high"  v-model="newItemPriority">
    Alta
</label>
{{ newItemPriority == 'low' ? '🍧': '🔥'}}
<ul>
 <li v-for="(item, i) in items" :key="item.id"> {{ i+1 }} {{ i%2==0?'🔥':'🛍' }} {{ item.label }}</li>
</ul>
</template>

<style scoped>
.shopping-cart-icon {
 font-size: 2rem; 
}
</style>
