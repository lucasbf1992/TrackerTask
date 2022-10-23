<template>
    <header>
        <div class="logo">
            <img class='imagem' src="../assets/logo.png" alt="Logo">
        </div>
        <div>
          <button class="button is-rounded is-warning" @click="alterarTema">
            {{ textoBotao }}
          </button>
        </div>
    </header>
</template>

<script>
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'BarraLateral',
  emits: ['temaAlterado'],
  data () {
    return {
      modoEscuro: false
    }
  },
  computed: {
    textoBotao() {
      if (this.modoEscuro) {
        return 'Desativar Modo Escuro'
      }

      return 'Ativar Modo Escuro'
    }
  },
  methods: {
    alterarTema() {
      this.modoEscuro = !this.modoEscuro
      this.$emit('temaAlterado', this.modoEscuro)
    }
  }
})
</script>

<style scoped>
    header {
      background: #0d3b65;
      width: 100%;
      height: 100vh;
      text-align: center;
    }

    .logo {
      padding: 4rem;
    }

    @media only screen and (max-width: 760px) {
        header {
            padding: 2.5rem;
            height: 10rem;
        }

      .logo {
        padding: 0.2rem;
      }

      .imagem {
        height: 2rem;
      }
    }
</style>
 