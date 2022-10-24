<template>
  <main class="columns is-gapless is-multiline" :class="{ 'modo-escuro': modoEscuro }">
    <div class="column is-one-quarter">
      <BarraLateral
        @temaAlterado="trocarTema"
      />
    </div>

    <div class="column is-three-quarter conteudo m-1">
      <FormularioTarefa @salvarTarefa="salvar" />
      <div class="">
        <ListaTarefas v-for="(tarefa, index) in tarefas" :key="index"
          :tarefa="tarefa"
          :chave="index"
          @exclusaoTarefa="excluir"
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
    excluir(chave) {
      this.tarefas.splice(chave, 1)
    },
    trocarTema(modoEscuro) {
      this.modoEscuro = modoEscuro
    }
  },
  watch: {
    tarefas: {
      deep: true,
      handler() {
        localStorage.setItem('tarefas', JSON.stringify(this.tarefas))
      }
    }
  },
  created() {
    const json = localStorage.getItem('tarefas')
    const tarefas = JSON.parse(json)

    if (Array.isArray(tarefas)) {
      this.tarefas = tarefas

      return
    }

    this.tarefas = []
  }
}
</script>

<style>
  main {
    --bg-primario: var(--bg-primario);
    --texto-primario: #000
  }

  main.modo-escuro {
    --bg-primario: #2b2d42;
    --texto-primario: #ddd
  }
</style>
