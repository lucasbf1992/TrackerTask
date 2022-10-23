<template>
  <main class="columns is-gapless is-multiline" :class="{ 'modo-escuro': modoEscuro }">
    <div class="column is-one-quarter">
      <BarraLateral
        @temaAlterado="trocarTema"
      />
    </div>

    <div class="column is-three-quarter conteudo">
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
      tarefas: [],
      modoEscuro: false,
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
    },
    trocarTema(modoEscuro) {
      this.modoEscuro = modoEscuro
    }
  }
}
</script>

<style>
  .lista {
    padding: 1.25rem;
  }

  main {
    --bg-primario: #fff;
    --texto-primario: #000
  }

  main.modo-escuro {
    --bg-primario: #2b2d42;
    --texto-primario: #ddd
  }

  .conteudo {
    background-color: var(--bg-primario);
  }
</style>
