<template>
  <main class="columns is-gapless is-multiline" :class="{ 'modo-escuro': modoEscuroAtivo }">
    <div class="column is-one-quarter">
      <BarraLateral @aoTemaAlterado="trocarTema"/>
    </div>
    <div class="column is-three-quarter conteudo">
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
      tarefas: [] as ITarefa[],
      modoEscuroAtivo: false
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
    },
    trocarTema(modoEscuroAtivado: boolean){
      this.modoEscuroAtivo = modoEscuroAtivado
    }
  }
});
</script>

<style>
  .lista{
    padding: 1.25rem;
  }
  main{
    --bg-primario: #fff;
    --texto-primario: #000;
  }
  main.modo-escuro{
    --bg-primario: #2b2d42;
    --texto-primario: #ddd;
  }
  .conteudo{
    background-color: var(--bg-primario);
  }
</style>
