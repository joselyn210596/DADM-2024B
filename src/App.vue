<script setup>
import{ref} from 'vue';
const header = ref('App lista de compras');
const items = ref([
    {id:'0', label: '10 bolillos'},
    {id:'1', label: '1 lata de frijoles'},
    {id:'2', label: '1 nutella'},
    {id:'3', label: '1 chela'}
    
]);
</script>

<template>
<h1> 
    <i class="material-icons shopping-cart-icon">local_mall </i>
    {{ header }}
</h1>
<ul>
 <li v-for="item in items" :key="item.id"> 👜{{ item.label }}</li>
</ul>
</template>

<style scoped>
.shopping-cart-icon {
 font-size: 2rem; 
}
</style>
