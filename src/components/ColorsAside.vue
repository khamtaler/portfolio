<script setup>
import ColorButton from './ColorButton.vue';
import languageSwitch from './languageSwitch.vue';
</script>
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
		<languageSwitch />
		<!-- <ColorButton
			:class="{ active: active === 'colorfule' }"
			colorClass="button--color---colorful"
			title="colorfule"
			@click="changeColor(`colorfule`)"
		/> -->
	</aside>
</template>

<script>
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
		languageSwitch,
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

.colorMenu .active::before {
	content: '';
	display: inline-block;
	position: absolute;
	background: #1f1f1f;
	width: 5px;
	height: 5px;
	border-radius: 50%;
}

.dark {
	.colorMenu .active::before {
		background: #fff;
	}
}

@media (min-width: 1320px) {
	.colorMenu {
		left: calc(-1 * (100vw - 100%) / 2);
	}
	.colorMenu .active {
		left: 15px;
	}
}
@media (min-width: 841px) {
	.colorMenu {
		top: 50vh;
		transform: translateY(-50%);
		left: calc((-1 * (100vw - 100%) / 2) + 15px);
		flex-direction: column;
	}
	.colorMenu .active {
		left: 12px;
	}
	.colorMenu .active::before {
		left: -12px;
		top: 50%;
		transform: translateY(-50%);
	}
	.languageMenu--label.active {
		left: 10px;
	}
	.languageMenu--label.active::before {
		left: -10px;
		top: 50%;
		transform: translateY(-50%);
	}
}
@media (max-width: 840px) {
	.colorMenu .active:before {
		top: -12px;
		left: 50%;
		transform: translateX(-50%);
	}
	.colorMenu .active {
		top: 10px;
	}
}

@media (max-width: 840px) {
	.languageMenu--label.active:before {
		top: -10px;
		left: 50%;
		transform: translateX(-50%);
	}
	.languageMenu--label.active {
		top: 10px;
	}
}
</style>
