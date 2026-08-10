<template>
    <div class="tarefa">
        <h4 class="tarefa-titulo">{{ titulo }}</h4>
        <p class="tarefa-descricao">{{ descricao }}</p>
        <button class="btn btn-primary">Concluir</button>
    </div>
</template>
<script setup>
    const props = defineProps({
        titulo: String,
        descricao: String
    })
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
        width: 400px;
        height: 150px;
        text-align: center;
        margin-top: 20px;
    }
    .btn{
        width: 100px;
    }

</style>

