<script setup>
import PlanpickerItem from './planpickerItem.vue';
import {ref, onMounted, onUnmounted} from 'vue';
// creando una referenci creativa para almacenar el plan seleccionado
const selectedPlan = ref(null);
const plans= ref(['El cafetero','El chelero','El intelectual']); 
const selectPlan=(name)=>{
// almacenar el plan seleccionado
selectedPlan.value = name;
};  
const plansWrapper= ref(null);

//Intentando obtener la referencia al elemento .plans
console.log("termina de ejecutar el script setup 😅");
//registrando el hook mounted
onMounted(() => {
    console.log("el componente PlanPicker se ha montado");
    console.log(plansWrapper.value);
 });

 // registrando el hook unmounted
 onUnmounted(()=> {
    console.log("El componente Planpicker se ha desmontado 🙄");
 });

</script>

<template>
    <div ref="plansWrapper" class="plans">
    <PlanpickerItem v-for="plan in plans"
    :key="plan" :name="plan" 
    @select="selectPlan"
    :select-plan="selectedPlan"/>
     
    </div>
    
</template>


<style scoped>

</style>