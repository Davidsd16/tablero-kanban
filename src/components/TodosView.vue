<!-- Este bloque contiene la lógica del componente utilizando la sintaxis <script setup> -->
<script setup>

// Definición de una variable reactiva 'boards' utilizando Vue 3 Composition API
let boards = reactive([
    // Primer objeto que representa un tablero
    {
        // Generación de un ID único para el tablero utilizando la librería crypto
        id: crypto.randomUUID(),
        // Nombre del tablero
        name: 'tablero 1',
        // Lista de items en el tablero
        items: [
            // Primer item del tablero
            {
                // Generación de un ID único para el item utilizando la librería crypto
                id: crypto.randomUUID(),
                // Título del item
                titulo: "Feature de archivos"
            },
            // Segundo item del tablero
            {
                // Generación de un ID único para el item utilizando la librería crypto
                id: crypto.randomUUID(),
                // Título del item
                titulo: "Resolver bug"
            }
        ]
    },
    // Segundo objeto que representa otro tablero
    {
        // Generación de un ID único para el tablero utilizando la librería crypto
        id: crypto.randomUUID(),
        // Nombre del tablero
        name: 'tablero 2',
        // Lista de items en el tablero
        items: [
            // Primer item del tablero
            {
                // Generación de un ID único para el item utilizando la librería crypto
                id: crypto.randomUUID(),
                // Título del item
                titulo: "Mandar reporte"
            },
            // Segundo item del tablero
            {
                // Generación de un ID único para el item utilizando la librería crypto
                id: crypto.randomUUID(),
                // Título del item
                titulo: "Code review"
            }
        ]
    }
]);


</script>

<!-- Este bloque contiene la estructura visual del componente -->
<template>
<!-- Aquí se define la estructura visual del componente -->
Hola Mundo
</template>

<!-- Este bloque contiene las reglas de estilo CSS específicas del componente -->
<style scoped></style>
