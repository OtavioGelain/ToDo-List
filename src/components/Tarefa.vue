<template>
    <div class="tarefa">
        <div>
            <h2 class="tarefa-titulo">{{ nome }}</h2>
            <p class="tarefa-descricao">{{ descricao }}</p>
        </div>
        <button class="btn btn-success" @click="concluirTarefa">Concluir Tarefa</button>

    </div>
</template>
<script>
    export default {
        props: {
            id: Number,
            nome: String,
            descricao: String
            //esta pegando as props do componente pai

        },
        methods: {
            concluirTarefa(){
                this.$emit('concluir-tarefa', this.id)
                //Ele esta avisando que o usuario clicou no botao de concluir tarefa
            }
        }
    }
</script>
<style>
    .tarefa{
        display: flex;
        flex-direction: row;
        justify-content: space-between;
        text-align: center;
        background-color: #f5f5f5;
        border: 1px solid #ccc;
        border-radius: 5px;
        width: 400px;
        height: 150px;
        margin-bottom: 20px;
    }

    .tarefa > div {
        flex: 1;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }

    .btn{
        margin: 10px;
        width: 150px;
        align-self: center;
    }
    .tarefa-descricao{
        overflow-wrap: break-word;
        word-break: break-word;
    }
    .tarefa-titulo{
        font-weight: bold;
    }
</style>