<script>
import CharacterCard from "./components/CharacterCard.vue"
import AppSearch from "./components/AppSearch.vue"

import axios from 'axios'; //importo Axios
import { store } from "./store.js" //state management

export default {
	components: {
		CharacterCard,
		AppSearch
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
			let indirizzo = this.store.apiUrl;

			if (this.store.searchString.length) {
				indirizzo += `?name=${this.store.searchString}`;
			}

			console.log("Richiama: ", indirizzo);

			axios.get(indirizzo).then(risultato => {
				// v. anche risultato.data.info 
				this.store.personaggi = risultato.data.results;
			}).catch(error => {
				this.store.personaggi = [];
				console.error("Non lo so Rick...");
			});
		}
	}
}
</script>

<template>
	<header>
		<AppSearch @search="getCharacters" />
	</header>
	<main>
		<!-- Attenzione: ho salvato i personaggi recuperati con axios nello store -->
		<!-- ma passo alla card il singolo personaggio, tramite props -->
		<CharacterCard v-for="personaggio in store.personaggi" :info="personaggio" />
		<p v-if="store.personaggi.length == 0">Nessun risultato</p>
	</main>
</template>

<style lang="scss">
@use './styles/general.scss';
</style>

<style scoped lang="scss">
// @use './styles/partials/variables' as *;

main {
	width: 80%;
	margin: 0 auto;

	display: flex;
	flex-wrap: wrap;
	// background: $themeColorDark;

	p {
		background: yellow;
	}
}
</style>