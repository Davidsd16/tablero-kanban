<!-- Importa reactive de la librería Vue 3 -->
<script setup>

    import { reactive } from 'vue';
    // Importa el componente InputNew
    import InputNew from "./InputNew.vue";

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

    // Función para manejar la creación de un nuevo ítem
    function handleNewItem(text, board){
        // Agrega un nuevo ítem al tablero especificado
        board.items.push({
            // Genera un ID único para el ítem utilizando la librería crypto
            id: crypto.randomUUID(),
            // Establece el título del ítem como el texto proporcionado
            title: text
        })
    }

    // Función para manejar la creación de un nuevo tablero
    function handleNewBoard(){
        // Solicita al usuario el nombre del nuevo tablero mediante un cuadro de diálogo
        const name = prompt('Name of the board')

        // Verifica si se proporcionó un nombre válido para el tablero
        if (name) { 
            // Agrega un nuevo tablero a la lista de tableros
            boards.push({
                // Genera un ID único para el tablero utilizando la librería crypto
                id: crypto.randomUUID(),
                // Establece el nombre del tablero como el nombre proporcionado
                name: name,
                // Inicializa la lista de ítems del tablero como vacía
                items: [],
            });
        }
    }

    function startDrag(event, board, item){
        event.dataTransfer.setData(
            'text/plain',
            JSON.stringify({ boardID: board.id, itemID: item.id})
        );
    }

    function onDrop(event, destination){
        const {boardId, itemID} = JSON.parse(
            event.dataTransfer.getData('text/plain')
        );
    }

   // console.log(boardId, itemID);

</script>

<!-- Este bloque contiene la estructura visual del componente -->
<template>
    <!-- Aquí se define la estructura visual del componente -->
    <nav>
        <ul>
            <!-- Botón para crear un nuevo tablero -->
            <li><a href="#" @click.prevent="handleNewBoard">Create board</a></li>
        </ul>
    </nav>

    <!-- Contenedor de tableros -->
    <div class="boards-container">
        <!-- Contenedor de tableros -->
        <div class="boards">
            <!-- Iteración sobre cada tablero -->
            <div class="board"
                @drop="onDrop($event, board, item)"
                @dragover.prevent
                v-for="board in boards"
                :key="board.id"
            >
                <!-- Nombre del tablero -->
                <div>{{ board.name }}</div>
                
                <!-- Componente InputNew para agregar nuevos ítems -->
                <InputNew @on-new-item="(text) => handleNewItem(text, board)"/> 

                <!-- Contenedor de ítems -->
                <div class="items">
                    <!-- Iteración sobre cada ítem del tablero -->
                    <div class="item" draggable="true" @dragstart="startDrag($event, board, item)" v-for="item in board.items" :key="item.id">
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
    /* Estilos para el contenedor de tableros */
    .boards {
        display: flex;
        gap: 10px;
    }

    /* Estilos para los tableros */
    .board {
        max-width: 300px;
        padding: 10px;
        background: rgb(239, 20, 239); /* Fondo de color para los tableros */
    }

    /* Estilos para los ítems */
    .items {
        display: flex;
        flex-direction: column;
        gap: 5px;
    }

    /* Estilos para los ítems */
    .item {
        background: rgb(255, 255, 80);
        padding: 10px;
        box-sizing: border-box;
    }
</style>
