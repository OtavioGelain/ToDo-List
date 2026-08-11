<template>
    <div class="tarefa">
        <h4 class="tarefa-titulo">{{ titulo }}</h4>
        <p class="tarefa-descricao">{{ descricao }}</p>
        <button class="btn btn-primary" @click="concluir">Concluir</button>
    </div>
</template>
<script setup>
    const props = defineProps({
        id: Number,
        titulo: String,
        descricao: String
    })
    const emit = defineEmits(['concluir'])
    function concluir() {
        emit('concluir', props.id)
    }
</script>   
<style>
    .tarefa{
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        background-color: aliceblue;
        border-radius: 10px;
        border: solid 1px #ccc;
        width: 500px;
        height: 200px;
        text-align: center;
        margin-top: 20px;
    }
    .btn{
        width: 100px;
    }

</style>

