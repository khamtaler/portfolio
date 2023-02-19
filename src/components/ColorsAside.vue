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
		<ColorButton
			:class="{ active: active === 'colorfule' }"
			colorClass="button--color---colorful"
			title="colorfule"
			@click="changeColor(`colorfule`)"
		/>
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
	flex-direction: row;
	gap: 20px;
	z-index: 2;
	position: absolute;
	top: 15px;
	left: 70px;
}
.colorMenu .active {
	top: 7px;
}
@media (min-width: 1320px) {
	.colorMenu {
		left: -15px;
	}
	.colorMenu .active {
		left: 15px;
	}
}
@media (min-width: 841px) {
	.colorMenu {
		top: 50px;
		left: 10px;
		flex-direction: column;
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
