<template>
  <BoxTarefa>
    <div class="columns">
      <div class="column is-7">
        {{tarefa.descricaoTarefa || 'Tarefa sem descrição' }}
      </div>
      <div class="column">
        <CronometroTarefa :tempo-em-segundos=tarefa.tempoTarefa>
        </CronometroTarefa>
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
  components: {BoxTarefa, CronometroTarefa},
  props: {
    tarefa: {
      type: Object,
      required: true
    }
  }
})

</script>

<style scoped>

</style>