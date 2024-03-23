<script setup>
    import { reactive } from 'vue'; // Importa reactive de la librería Vue 3
    import { crypto } from 'crypto'; // Importa crypto
</script>

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
    <nav>
        <ul>
            <li><a href="#">Create board</a></li>
        </ul>
    </nav>

<!-- Contenedor de tableros -->
<div class="boards-container">
    <!-- Contenedor de tableros -->
    <div class="boards">
        <!-- Iteración sobre cada tablero -->
        <div class="board" v-for="board in boards" :key="board.id">
            <!-- Nombre del tablero -->
            <div>{{ board.name }}</div>
            <!-- Contenedor de ítems -->
            <div class="items">
                <!-- Iteración sobre cada ítem del tablero -->
                <div class="item" v-for="item in board.items" :key="item.id">
                    <!-- Título del ítem -->
                    {{ item.titulo }}
                </div>
            </div>
        </div>
    </div>
</div>

</template>



<!-- Este bloque contiene las reglas de estilo CSS específicas del componente -->
<style scoped></style>
