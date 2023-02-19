<template>
	<aside class="colorMenu">
		<ColorButton
			:class="{ active: active === 'light' }"
			colorClass="button--color---light"
			title="light"
			@click="changeColor(`light`)"
		/>
		<ColorButton
			:class="{ active: active === 'dark' }"
			colorClass="button--color---dark"
			title="dark"
			@click="changeColor(`dark`)"
		/>
		<!-- <ColorButton
			:class="{ active: active === 'colorful' }"
			colorClass="button--color---colorful"
			title="colorful"
			@click="changeColor(`colorful`)"
		/> -->
	</aside>
</template>

<script>
import ColorButton from './ColorButton.vue';
export default {
	data() {
		return {
			color: 'dark',
			active: 'dark',
		};
	},
	methods: {
		changeColor(title) {
			document.body.classList.remove(this.color);
			this.color = title;
			document.body.classList.add(this.color);
			this.active = title;
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
	z-index: 2;
	position: absolute;
	top: 50px;
	left: 10px;
}
.colorMenu .active {
	left: 15px;
}
@media (min-width: 1320px) {
	.colorMenu {
		left: -15px;
	}
}
@media (max-width: 840px) {
	.colorMenu {
		top: 70px;
	}
}
// 	.colorMenu {
// 		top: 10px;
// 		right: 20px;
// 		left: unset;
// 		flex-direction: row;
// 	}
// }
</style>
