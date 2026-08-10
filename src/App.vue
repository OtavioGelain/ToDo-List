<script setup>
    import Tarefa from './components/Tarefa.vue'
    const data = {
        tarefa: {
            id: 1,
            titulo: 'Estudar Vue.js',
            descricao: 'Aprender os conceitos básicos do Vue.js e criar um projeto simples.',
        }
    }
</script>

<template>
    <div class="container">
        <h1 class="mt-4">Lista de Tarefas</h1>
        <div>
            <p>Titulo da Tarefa</p>
            <input type="text" class="form-control" >
        </div>
        <div>
            <p>Descrição da Tarefa</p>
            <input type="text" class="form-control" >
        </div>
        <button class="btn btn-primary">Adicionar Tarefa</button>
    </div>
  <Tarefa 
    :titulo="data.tarefa.titulo" 
    :descricao="data.tarefa.descricao" 
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
