<template>
    <h2>Tarefas Concluidas</h2>
    <div class="tarefa">
        <h4>{{ nome }}</h4>
        <p class="tarefa-descricao">{{ descricao }}</p>
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
    .tarefa{
        display: flex;
        flex-direction: row;
        justify-content: space-between;
        text-align: center;
        background-color: #02b002;
        color: black;
        border: 1px solid #ccc;
        border-radius: 5px;
        width: 400px;
        height: 150px;
        margin-bottom: 20px;
    }
    .tarefa-descricao{
        overflow-wrap: break-word;
        word-break: break-word;
    }
</style>