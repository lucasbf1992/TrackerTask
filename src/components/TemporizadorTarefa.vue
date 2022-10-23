<template>
  <div class="is-flex is-align-iteems-center is-justify-content-space-between">
    <CronometroTarefa
        :tempo-em-segundos="tempoEmSegundos"
    />
    <button class="button is-rounded is-success" :class="classe" @click='iniciar' :disabled="cronometroAtivo">
      <span class="icon">
        <i class="fas fa-play"></i>
      </span>
      <span>Iniciar</span>
    </button>
    <button class="button is-rounded is-danger" @click="finalizar" :disabled="!cronometroAtivo">
      <span class="icon">
        <i class="fas fa-stop"></i>
      </span>
      <span>
        Parar
      </span>
    </button>
  </div>
</template>

<script>
import CronometroTarefa from "@/components/CronometroTarefa";
import {defineComponent} from "vue";

export default defineComponent({
  name: "TemporizadorTarefa",
  emits: ['temporizadorFinalizado'],
  components: {
    CronometroTarefa
  },
  data() {
    return {
      tempoEmSegundos: 0,
      cronometro: 0,
      cronometroAtivo: false,
      classe: null
    }
  },
  methods: {
    iniciar() {
      this.cronometroAtivo = true
      this.classe = 'is-loading'

      this.cronometro = setInterval(() => {
        this.tempoEmSegundos++
      }, 1000)
    },

    finalizar() {
      this.cronometroAtivo = false
      this.classe = ''

      clearInterval(this.cronometro)

      this.$emit('temporizadorFinalizado', this.tempoEmSegundos)

      this.tempoEmSegundos = 0
    }
  }
})
</script>

<style scoped>

</style>