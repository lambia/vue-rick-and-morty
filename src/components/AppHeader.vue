<script>
import { store } from "../store.js"

export default {
    name: "AppHeader",
    props: {
        title: String,
        links: Array
    },
    data() {
        return {
            store
        }
    },
    mounted() {
        console.log("AppHeader caricato con store", this.store);
    }
}
</script>

<template>
    <header>
        <h1>{{ title }}</h1>
        <div>Inserisci il tuo nome utente: <input v-model="store.nomeUtente" /></div>
        <h2>Benvenuto, {{ store.nomeUtente }}</h2>
        <nav>
            <a href="#" v-for="link in links">{{ link }}</a>
        </nav>
    </header>
</template>

<style scoped>
header {
    background: crimson;
    color: white;
}

nav {
    display: flex;
    justify-content: space-between;
}
</style>