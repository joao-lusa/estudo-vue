<template>
    <Caixa>
        <div class="columns">
            <div class="column is-7">{{tarefa.descricao || 'Tarefa sem descrição'}}</div>
            <div class="column">
                <Contador :tempoEmSegundos="tarefa.duracaoEmSegundos"/>
            </div>
        </div>
    </Caixa> 
</template>

<script lang="ts">
import {defineComponent, PropType} from 'vue'
import ITarefa from '@/interfaces/ITarefa'
import Caixa from './Caixa.vue'
import Contador from './Contador.vue'


export default defineComponent({
    name: 'TarefaFeita',
    components: {
        Contador,
        Caixa
    },
    props: {
        tarefa:{
            type: Object as PropType<ITarefa>,
            required: true
        }
    }
})
</script>
