<script>
import CharacterCard from "./components/CharacterCard.vue"

import axios from 'axios'; //importo Axios
import { store } from "./store.js" //state management

export default {
	components: {
		CharacterCard
	},
	data() {
		return {
			store,
		}
	},
	mounted() {
		this.getCharacters();
	},
	methods: {
		getCharacters() {
			axios.get(this.store.apiUrl).then(risultato => {
				// v. anche risultato.data.info 
				this.store.personaggi = risultato.data.results;
				this.page++;
			});
		},
	}
}
</script>

<template>
	<main>
		<!-- Attenzione: ho salvato i personaggi recuperati con axios nello store -->
		<!-- ma passo alla card il singolo personaggio, tramite props -->
		<CharacterCard v-for="personaggio in store.personaggi" :info="personaggio" />
	</main>
</template>

<style scoped>
main {
	width: 80%;
	margin: 0 auto;

	display: flex;
	flex-wrap: wrap;
}
</style>