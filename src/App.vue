<script setup>
import ContactForm from './components/ContactForm.vue';
import ColorsAside from './components/ColorsAside.vue';
import Tile from './components/Tile.vue';
import Menu from './components/Menu.vue';
</script>

<template>
	<ColorsAside />
	<Menu />
	<main class="main">
		<Tile>
			<ContactForm />
		</Tile>
	</main>
</template>

<script>
export default {
	components: {
		Menu,
		ContactForm,
		ColorsAside,
	},
};
</script>

<style lang="scss" scoped>
.main {
	display: flex;
	align-items: center;
	justify-content: center;
	height: 100%;
	width: 100%;
}
</style>
