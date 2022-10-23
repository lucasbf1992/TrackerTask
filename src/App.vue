<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <BarraLateral/>
    </div>

    <div class="column is-three-quarter">
      <FormularioTarefa @salvarTarefa="salvar" />
      <div>
        <ListaTarefas v-for="(tarefa, index) in tarefas" :key="index"
          :tarefa="tarefa"
        />
      </div>
      <BoxTarefa v-if="listaEstaVazia">
        Nenhuma tarefa cadastrada! :(
      </BoxTarefa>
    </div>
  </main>
</template>

<script lang="js">
import BarraLateral from "./components/BarraLateral.vue";
import FormularioTarefa from "./components/FormularioTarefa.vue";
import ListaTarefas from "@/components/ListaTarefas";
import BoxTarefa from "@/components/BoxTarefa";

export default {
  name: 'App',
  components: {
    BoxTarefa,
    BarraLateral,
    FormularioTarefa,
    ListaTarefas,
  },
  data () {
    return {
      tarefas: []
    }
  },
  computed: {
    listaEstaVazia() {
      return this.tarefas.length === 0
    }
  },
  methods: {
    salvar(tarefa) {
      this.tarefas.push(tarefa)
    }
  }
}
</script>

<style>
  .lista {
    padding: 1.25rem;
  }
</style>
