<script setup>
import ContactForm from './components/ContactForm.vue';
import ColorsAside from './components/ColorsAside.vue';
</script>

<template>
	<ColorsAside />
	<main>
		<ContactForm />
	</main>
</template>

<script>
export default {
	components: {
		ContactForm,
		ColorsAside,
	},
};
</script>

<style lang="scss" scoped></style>
