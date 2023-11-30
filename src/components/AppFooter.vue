<script>
import { store } from "../store.js"

export default {
    name: "AppFooter",
    props: {
        links: Array
    },
    data() {
        return {
            store
        }
    }
}
</script>

<template>
    <footer>
        <h2>Ciao {{ store.nomeUtente }}, questo è il footer:</h2>
        <nav>
            <a href="#" v-for="link in links">{{ link }}</a>
        </nav>
    </footer>
</template>

<style scoped>
footer {
    background: teal;
    color: white;
}
</style>