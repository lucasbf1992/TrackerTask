<template>
    <div class="box formulario">
        <div class="columns">
            <div class="column is-8" role="form" aria-label="Formulário para criação de tarefas">
                <input type="text" class="input" placeholder="Digite aqui sua tarefa" v-model="descricaoTarefa">
            </div>
            <div class="column">
              <TemporizadorTarefa @temporizadorFinalizado="registrarTarefa"/>
            </div>
        </div>
    </div>
</template>

<script>
import { defineComponent } from 'vue'
import TemporizadorTarefa from './TemporizadorTarefa'

export default defineComponent({
    name: 'FormularioTarefa',
    components: {
      TemporizadorTarefa
    },
    emits: ['salvarTarefa'],
    data() {
        return {
          descricaoTarefa: ''
        }
    },
    methods: {
      registrarTarefa(tempoDecorrido) {
        this.$emit('salvarTarefa', {
          tempoTarefa: tempoDecorrido,
          descricaoTarefa: this.descricaoTarefa
        })

        this.descricaoTarefa = ''
      }
    }
})
</script>

<style>
  .formulario {
    color: var(--texto-primario);
    background-color: var(--bg-primario);
  }
  .box {
    border: none;
  }
</style>