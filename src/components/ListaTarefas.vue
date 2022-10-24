<template>
  <BoxTarefa>
    <div class="columns">
      <div class="column is-4">
        {{tarefa.descricaoTarefa || 'Tarefa sem descrição' }}
      </div>
      <div class="column">
        <CronometroTarefa :tempo-em-segundos=tarefa.tempoTarefa>
        </CronometroTarefa>
      </div>
      <div class="column">
        <button class="button is-rounded is-danger" @click="excluirTarefa(chave)">
          <span class="icon">
            <i class="fas fa-trash"></i>
          </span>
        </button>
      </div>
    </div>
  </BoxTarefa>
</template>

<script>
import {defineComponent} from "vue";
import CronometroTarefa from "@/components/CronometroTarefa";
import BoxTarefa from "@/components/BoxTarefa";

export default defineComponent({
  name: "ListaTarefas",
  emits: ["exclusaoTarefa"],
  components: {BoxTarefa, CronometroTarefa},
  props: {
    chave: {
      type: Number,
      required: true
    },
    tarefa: {
      type: Object,
      required: true
    }
  },
  methods: {
    excluirTarefa(chave) {
      this.$emit('exclusaoTarefa', chave)
    }
  }
})

</script>

<style scoped>

</style>