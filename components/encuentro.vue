<!-- components/Encuentro.vue -->
<template>
    <div class="flex items-center justify-between p-4 bg-white rounded-lg shadow">
      <div @click="setGanador(participante1)" :class="{'font-bold': ganador === participante1}">
        {{ participante1 }}
      </div>
      <span>vs</span>
      <div @click="setGanador(participante2)" :class="{'font-bold': ganador === participante2}">
        {{ participante2 }}
      </div>
      <div v-if="ganador" class="ml-4 text-green-500">
        Ganador: {{ ganador }}
      </div>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  
  const props = defineProps({
    participante1: String,
    participante2: String,
  });
  
  const ganador = ref('');
  
  const setGanador = (participante) => {
    ganador.value = participante;
  };
  </script>
  
  <style scoped>
  /* Estilos adicionales si son necesarios */
  </style>
  