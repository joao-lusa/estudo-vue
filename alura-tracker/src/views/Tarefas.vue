<template>
    <Formulario @aoSalvarTarefa="salvarTarefa"/>
    <div class="lista">
    <Caixa v-if="listaEstaVazia">
        Você não esta muito produtivo Hoje :(
    </Caixa>        
    <Tarefa v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa" />
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import Formulario from '../components/Formulario.vue'
import Tarefa from '../components/Tarefa.vue'
import ITarefa from '../interfaces/ITarefa'
import Caixa from '../components/Caixa.vue'

export default defineComponent({
  name: 'App',
  components:{
    Formulario,
    Tarefa,
    Caixa
  },
  data(){
    return{
      tarefas: [] as ITarefa[],
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
    },
});
</script>
