<template>
    <header>
        <div class="logo">
            <img src="../assets/logo.png" alt="Logo">
        </div>
    </header>
</template>

<script>
import { defineComponent } from 'vue'

export default defineComponent({
    name: 'BarraLateral',
})
</script>

<style scoped>
    header {
        background: #0d3b65;
        width: 100%;
        height: 100vh;
    }

    .logo {
      padding: 4rem;
    }

    @media only screen and (max-width: 760px) {
        header {
            padding: 2.5rem;
            height: auto;
        }
    }
</style>
 