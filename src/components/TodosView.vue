<script setup>

    import { reactive } from 'vue'; // Importa reactive de la librería Vue 3


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
                    title: "Feature de archivos"
                },
                // Segundo item del tablero
                {
                    // Generación de un ID único para el item utilizando la librería crypto
                    id: crypto.randomUUID(),
                    // Título del item
                    title: "Resolver bug"
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
                    title: "Mandar reporte"
                },
                // Segundo item del tablero
                {
                    // Generación de un ID único para el item utilizando la librería crypto
                    id: crypto.randomUUID(),
                    // Título del item
                    title: "Code review"
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
                        {{ item.title }}
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<!-- Este bloque contiene las reglas de estilo CSS específicas del componente -->
<style scoped>
    /* Estilos para los tableros */
    .boards {
        display: flex;
        gap: 10px;
        max-width: 300px;
        margin-right: 20px;
    }
    /* Estilos para el contenedor de tableros */
    .boards {
        display: flex;
        gap: 10px;
        background: rgb(188, 211, 33);
        padding: 10px;
    }
</style>
