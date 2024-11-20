<script setup>
import PlanpickerItem from './planpickerItem.vue';
import planpickerItem from './planpickerItem.vue';
import {ref, onMounted} from 'vue';
// creando una referenci creativa para almacenar el plan seleccionado
const selectedPlan = ref(null);
const plans= ref(['El cafetero','El chelero','El intelectual']); 
const selectPlan=(name)=>{
// almacenar el plan seleccionado
selectedPlan.value = name;
};  
//Intentando obtener la referencia al elemento .plans
console.log("termina de ejecutar el script setup 😅");
//registrando el hook mounted
onMounted(() => {console.log("el componente PlanPicker se ha montado");
    console.log(document.querySelector('.plans'));
 });

</script>

<template>
    <div class="plans">
    <PlanpickerItem v-for="plan in plans"
    :key="plan" :name="plan" 
    @select="selectPlan"
    :select-plan="selectedPlan"/>
     
    </div>
    
</template>


<style scoped>

</style>