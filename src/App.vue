<!-- Este bloque contiene la lógica del componente utilizando la sintaxis <script setup> -->
<script setup>
// Aquí se importa el componente TodoView desde el archivo './components/TodosView.vue'
import TodoView from './components/TodosView.vue';
</script>

<!-- Este bloque contiene la estructura visual del componente -->
<template>
<!-- Aquí se define la estructura visual del componente -->
<!-- Se incluye el componente TodoView dentro de este template -->
<TodoView/>
</template>

<!-- Este bloque contiene las reglas de estilo CSS específicas del componente -->
<style scoped>
/* Aquí se pueden definir reglas de estilo CSS específicas del componente */
/* El atributo scoped asegura que las reglas de estilo solo se apliquen al componente actual */
</style>
