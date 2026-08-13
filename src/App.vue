<script>
    import Tarefa from './components/Tarefa.vue'
    import TarefasConcluidas from './components/TarefasConcluidas.vue';

    export default {
        name: 'App',
        components: {
            Tarefa,
            TarefasConcluidas
        },
        data() {
            return {
                nome: '',
                descricao: '',
                tarefas: [
                    {
                        id: 1,
                        nome: 'Tarefa 1',
                        descricao: 'Descrição da Tarefa 1',
                        concluida: false
                    }
                ]
            }
        },
        //methods é sempre onde ficam minhas funções
        methods: {
            adicionarTarefa(){
                const novaTarefa = {
                    id: this.tarefas.length + 1,
                    nome: this.nome,
                    descricao: this.descricao,
                    concluida: false
                }
                if(this.nome.trim() === '' || this.descricao.trim() === ''){
                    alert('Por favor, preencha todos os campos.')
                    return
                }
                this.tarefas.push(novaTarefa)
                this.nome = ''
                this.descricao = ''
            },
            concluirTarefa(id){
                //this.tarefas = this.tarefas.filter(tarefa => tarefa.id !== id)
                const tarefa = this.tarefas.find(t => t.id === id)
                if(tarefa){
                    tarefa.concluida = true
                }
                //esta removendo a tarefa que foi concluida
            },

        },
        computed: {
            tarefasConcluidas() {
                return this.tarefas.filter(tarefa => tarefa.concluida)
            },
            tarefasPendentes(){
                return this.tarefas.filter(tarefa => !tarefa.concluida)
            }
        }

    }
</script>
<template>
    <div class="app">
        <h1>Lista de Tarefas</h1>
        <div class="container-tarefaT">
            <label for="nome">Nome da Tarefa:</label>
            <input type="text" name="nome" id="nome" v-model="nome" />
        </div>
        <div class="container-tarefaD">
            <label for="descricao">Descrição da Tarefa:</label>
            <textarea name="descricao" id="descricao" cols="30" rows="10" v-model="descricao"></textarea>
        </div>
        <button class="btn btn-primary" @click="adicionarTarefa">Adicionar Tarefa</button>
    </div>
    <div class="lista-tarefas">
        <h2 class="lista-tarefas-pendente-titulo">Tarefas Pendentes</h2>
        <Tarefa
        v-for="tarefa in tarefasPendentes"
        :key="tarefa.id"
        :id="tarefa.id"
        :nome="tarefa.nome"
        :descricao="tarefa.descricao"
        :concluida="tarefa.concluida"
        @concluir-tarefa="concluirTarefa"
        />
    </div>
    <h4 v-if="tarefasPendentes.length === 0" class="alert alert-info">Nenhuma tarefa pendente.</h4>
    <div class="lista-tarefas-concluidas">
        <h2 class="tarefas-concluidas-titulo">Tarefas Concluidas</h2>
        <TarefasConcluidas
        v-for="tarefa in tarefasConcluidas"
        :key="tarefa.id"
        :id="tarefa.id"
        :nome="tarefa.nome"
        :descricao="tarefa.descricao"
        :concluida="tarefa.concluida"
        />
    </div>


</template>
<style>
    body {
        margin: 0;
        padding: 0;
        font-family: Arial, sans-serif;
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .app{
        background-color: #f2f2f2;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        height: 400px;
        width: 600px;
        border: solid 1px #ccc;
        border-radius: 10px;
        margin-top: 50px;
    }
    .lista-tarefas{
        display: flex;
        text-align: center;
        align-items: center;
        flex-direction: column;
        margin-top: 20px;
    }
    #descricao{
        width: 300px;
        height: 100px;
    }
    #nome{
        width: 300px;
    }
    .container-tarefaT, .container-tarefaD{
        display: flex;
        flex-direction: column;
        margin-bottom: 10px;
    }
    .alert{
        margin-top: 20px;
        text-align: center;
    }
    textarea{
        resize: none;
    }
    .tarefas-concluidas-titulo{
        text-align: center;
        margin-bottom: 25px;
    }
    .lista-tarefas-concluidas{
        display: flex;
        align-items: center;
        flex-direction: column;
   }
   .lista-tarefas-pendente-titulo{
        margin-bottom: 25px;
   }
</style>