<script setup>
import PlanpickerItem from './planpickerItem.vue';
import planpickerItem from './planpickerItem.vue';
import {ref} from 'vue';
const plans= ref(['El cafetero','El chelero','El intelectual']);      
</script>

<template>
    <div class="plans">
    <PlanpickerItem v-for="plan in plans"
    :key="plan" :name="plan" 
    @select="(name) =>{console.log(name)}"/>
     
    </div>
</template>


<style scoped>

</style>