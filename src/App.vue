<script setup>
    import Tarefa from './components/Tarefa.vue'
    import { ref } from 'vue'

    const titulo = ref('')
    const descricao = ref('')
    const tarefas = ref([
        {
            id: 1,
            titulo: 'Estudar Vue.js',
            descricao: 'Aprender os conceitos básicos do Vue.js e criar um projeto simples.',
        }
    ])
    function addTarefa(titulo, descricao) {
        const novaTarefa = {
            id: tarefas.length + 1,
            titulo: titulo,
            descricao: descricao
        }
        tarefas.value.push(novaTarefa)
    }
    function concluirTarefa(id) {
        tarefas.value = tarefas.value.filter(tarefa => tarefa.id !== id)
    }
    
</script>

<template>
    <div class="container">
        <h1 class="mt-4">Lista de Tarefas</h1>
        <div>
            <p>Titulo da Tarefa</p>
            <input type="text" class="form-control" v-model="titulo" >
        </div>
        <div>
            <p>Descrição da Tarefa</p>
            <input type="text" class="form-control" v-model="descricao" >
        </div>
        <button class="btn btn-primary" @click="addTarefa(titulo, descricao)">Adicionar Tarefa</button>
    </div>
  <Tarefa 
    v-for="tarefa in tarefas"
    :key="tarefa.id"
    :titulo="tarefa.titulo" 
    :descricao="tarefa.descricao" 
    :id="tarefa.id"
    @concluir="concluirTarefa"
    />
</template>
<style>
    body{
        background-color: #f8f9fa;
        display: flex;
        justify-content: center;
        gap: 50px;
    }
    .container{
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        gap: 10px;
    }
    .mt-4{
        margin-top: 20px;
        text-align: center;
    }
    .btn{
        width: 150px;
        margin-top: 10px;
    }
    
</style>
