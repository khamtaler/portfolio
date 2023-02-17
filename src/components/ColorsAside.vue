<template>
	<aside class="colorMenu">
		<ColorButton colorClass="button--color---light" title="light" @click="changeColor(`light`)" />
		<ColorButton colorClass="button--color---dark" title="dark" @click="changeColor(`dark`)" />
		<ColorButton
			colorClass="button--color---colorful"
			title="colorful"
			@click="changeColor(`colorful`)"
		/>
	</aside>
</template>

<script>
import ColorButton from './ColorButton.vue';
export default {
	data() {
		return {
			color: 'dark',
		};
	},
	methods: {
		changeColor(title) {
			document.body.classList.remove(this.color);
			this.color = title;
			document.body.classList.add(this.color);
		},
	},
	mounted() {
		document.body.classList.add(this.color);
	},
	components: {
		ColorButton,
	},
};
</script>

<style lang="scss" scoped>
.colorMenu {
	display: flex;
	flex-direction: column;
	gap: 20px;
	position: absolute;
	top: 50px;

	left: 10px;
}
@media (min-width: 1320px) {
	.colorMenu {
		left: -15px;
	}
}
</style>
