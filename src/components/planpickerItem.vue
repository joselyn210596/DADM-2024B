<template>
    <div @:click="selectPlan" 
    class="plan" 
    :class="{selected : isSelected}"
    >
      <div class="description">
        <span class="title">
          {{ name }} {{ isSelected ? '⭐' : '' }}
        </span>
      </div>
    </div>
  </template>
  
  <script setup>
  // importamos la funcion para crear propiedad computada
   import { computed } from 'vue';
  //Usando un macro para definir propiedades
   //defineProps(['name','planIcon']);
   const props = defineProps({name:{type: String, 
    required: true}, selectPlan: String });
   // definir event
   const emit = defineEmits(['select']);
   // funcion que permite cambiar el estado de la variable
   const selectPlan = () => {
    //emitir el evento de que el plan a sido seleccionado
    emit('select',props.name );
   };
   //creando una propiedad computada
   //para saber si el plan ha sido seleccionado
   const isSelected = computed( () => {
    return props.name === props.selectPlan;
   });
  </script>
  
  <style scoped>
  
  </style>