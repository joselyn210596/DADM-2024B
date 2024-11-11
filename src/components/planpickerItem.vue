<template>
    <div @:click="selectPlan" class="plan">
      <div class="description">
        <span class="title">
          {{ name }} {{ selected ? '⭐' : '' }}
        </span>
      </div>
    </div>
  </template>
  
  <script setup>
  // import ref
  import {ref} from 'vue';
  //Usando un macro para definir propiedades
   //defineProps(['name','planIcon']);
   const props = defineProps({name:{type: String, required: true} });
   // definir event
   const emit = defineEmits(['select']);
   // variable que permite recordar si el plan a sido seleccionado 
   const selected = ref(false);
   // funcion que permite cambiar el estado de la variable
   const selectPlan = () => {
    selected.value = true;
    //emitir el evento de que el plan a sido seleccionado
    emit('select',props.name );
   };
  </script>
  
  <style scoped>
  
  </style>