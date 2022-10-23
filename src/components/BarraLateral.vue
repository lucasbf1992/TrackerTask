<template>
    <header>
        <h1>
            <img src="../assets/logo.png" alt="Logo">
        </h1>
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

    @media only screen and (max-width: 760px) {
        header {
            padding: 2.5rem;
            height: auto;
        }
    }
</style>
 