<script>
import AppHeader from "./components/AppHeader.vue"
import AppFooter from "./components/AppFooter.vue"

export default {
	components: {
		AppHeader,
		AppFooter
	},
	data() {
		return {
			menuLinks: [
				"Home",
				"Chi Siamo",
				"Contatti"
			]
		}
	}
}
</script>

<template>
	<AppHeader title="Benvenuto in Rick and Morty" :links="menuLinks" />
	<main>
		Main Placeholder
	</main>
	<AppFooter :links="menuLinks" />
</template>

<style scoped></style>