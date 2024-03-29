<script setup>
    // Importa los métodos necesarios desde Vue
    import { ref, defineEmits } from "vue";

    // Crea una referencia reactiva llamada 'text' con un valor inicial vacío
    const text = ref('');

    // Define los eventos personalizados que puede emitir este componente
    const emits = defineEmits(['onNewItem']);

    // Función para manejar el envío del formulario
    function handleSubmit() {
        // Verifica si el contenido de 'text' no está vacío
        if (text.value !== '') {
            // Si 'text' no está vacío, emite el evento 'onNewItem' con el valor de 'text'
            emits('onNewItem', text.value)

            text.value = '';
        }
    }
</script>

<template>
    <!-- Formulario que ejecuta la función 'handleSubmit' al enviar -->
    <form action="" @submit.prevent="handleSubmit">
        <!-- Input vinculado a la referencia reactiva 'text' -->
        <input type="text" v-model="text">
    </form>
</template>

<style scoped>

    form {
        margin-bottom: 10px;
    }

    input {
        width: 100%;
        box-sizing: border-box;
    }
</style>
