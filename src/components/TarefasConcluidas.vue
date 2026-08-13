<template>
    <div class="tarefa-concluida">
        <h4 class="tarefa-concluida-titulo">{{ nome }}</h4>
        <p class="tarefa-concluida-descricao">{{ descricao }}</p>
    </div>
</template>
<script>
    export default {
        props: {
            id: Number,
            nome: String,
            descricao: String,
            concluida: Boolean
        }
    }
</script>
<style>
    .tarefa-concluida{
        display: flex;
        flex-direction: column;
        text-align: center;
        background-color: #2fe32f;
        color: black;
        border: 1px solid #ccc;
        border-radius: 5px;
        width: 400px;
        height: 150px;
        margin-bottom: 20px;
    }
    .tarefa-concluida-descricao{
        overflow-wrap: break-word;
        word-break: break-word;
    }
    .tarefa-concluida-titulo{
        margin-top: 15px;
        font-weight: bold;
    }
</style>