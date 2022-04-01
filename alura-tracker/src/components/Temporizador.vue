<template>
  <section class="is-flex is-align-items-center is-justify-content-space-between">
    <Contador :tempoEmSegundos="tempoEmSegundos"/>
    <Botao @clicado="iniciar" icone="fas fa-play" texto="play" :desabilitado="cronometroRodando" />
    <Botao @clicado="finalizar" icone="fas fa-stop" texto="stop" :desabilitado="!cronometroRodando" />
  </section>
</template>

<script>
import { defineComponent } from 'vue';
import Contador from "./Contador.vue";
import Botao from "./Botao.vue"

export default defineComponent({
    name: "TemporizadorDoCronometro",
    emits: ['aoTemporizadorFinalizado'],
    components:{
        Contador,
        Botao
    },
    data(){
        return {
            tempoEmSegundos: 0,
            cronometro: 0,
            cronometroRodando: false
        }
    },
    methods:{
        iniciar(){this.cronometroRodando = true

            this.cronometro = setInterval(()=>{
                this.tempoEmSegundos +=1
            },1000)
        },
        finalizar(){
            this.cronometroRodando = false
            clearInterval(this.cronometro)
            this.$emit('aoTemporizadorFinalizado', this.tempoEmSegundos)
            this.tempoEmSegundos = 0
        }
    }
});
</script>