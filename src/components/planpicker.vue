<script setup>
import PlanpickerItem from './planpickerItem.vue';
import planpickerItem from './planpickerItem.vue';
import {ref} from 'vue';
// creando una referenci creativa para almacenar el plan seleccionado
const selectedPlan = ref(null);
const plans= ref(['El cafetero','El chelero','El intelectual']); 
const selectPlan=(name)=>{
// almacenar el plan seleccionado
selectedPlan.value = name};    
</script>

<template>
    <div class="plans">
    <PlanpickerItem v-for="plan in plans"
    :key="plan" :name="plan" 
    @select="selectPlan"
    :select-plan="selectedPlan"/>
     
    </div>
    <p> {{ selectedPlan }}</p>
</template>


<style scoped>

</style>