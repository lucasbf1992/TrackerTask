<template>
  <section>
    <strong>
      {{ tempoDecorrido }}
    </strong>
  </section>
</template>

<script>
export default {
  name: "CronometroTarefa",
  props: {
    'tempoEmSegundos' : {
      type : Number,
      default : 0
    }
  },
  computed: {
    tempoDecorrido() {
      return new Date(this.tempoEmSegundos * 1000).toISOString().substr(11, 8)
    }
  }
}
</script>

<style scoped>
  section {
    padding-right: 1.5rem;
  }
</style>