<template>
  <main class="columns is-gasless is-multiline">
    <div class="column is-one-quarter">
      <BarraLateral />
    </div>
    <div class="column is-three-quarter">
      <Formulario @aoSalvarTarefa="salvarTarefa"/>
      <div class="lista">
        <Tarefa v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa" />
        <Caixa v-if="listaEstaVazia">
          Você não esta muito produtivo Hoje :(
        </Caixa>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue'
import Formulario from './components/Formulario.vue'
import Tarefa from './components/Tarefa.vue'
import ITarefa from './interfaces/ITarefa'
import Caixa from './components/Caixa.vue'

export default defineComponent({
  name: 'App',
  components:{
    BarraLateral,
    Formulario,
    Tarefa,
    Caixa
  },
  data(){
    return{
      tarefas: [] as ITarefa[]
    }
  },
  computed:{
    listaEstaVazia():boolean{
      return this.tarefas.length === 0
    }
  },
  methods:{
    salvarTarefa(tarefa: ITarefa){
      this.tarefas.push(tarefa)
    }
  }
});
</script>

<style>
  .lista{
    padding: 1.25rem;
  }
</style>
