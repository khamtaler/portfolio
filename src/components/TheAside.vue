<script setup>
import ColorMenuButton from './ColorMenuButton.vue';
import TheLanguageMenu from './TheLanguageMenu.vue';
</script>
<template>
	<aside class="aside">
		<ColorMenuButton
			:class="{ active: active === 'light' }"
			title="light"
			@click="changeColor(`light`)"
		/>
		<ColorMenuButton
			:class="{ active: active === 'dark' }"
			title="dark"
			@click="changeColor(`dark`)"
		/>
		<TheLanguageMenu />
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
		ColorMenuButton,
		TheLanguageMenu,
	},
};
</script>

<style lang="scss" scoped>
.aside {
	display: flex;
	flex-direction: row;
	gap: 20px;
	z-index: 2;
	position: absolute;
	top: 15px;
	left: 70px;
}

.active::before {
	content: '';
	display: inline-block;
	position: absolute;
	background: #1f1f1f;
	width: 5px;
	height: 5px;
	border-radius: 50%;
}

.dark {
	.active {
		&::before {
			background: #fff;
		}
	}
}

@media (min-width: 1320px) {
	.aside {
		left: calc(-1 * (100vw - 100%) / 2);
	}
	.active {
		left: 15px;
	}
}
@media (min-width: 841px) {
	.aside {
		top: 50vh;
		transform: translateY(-50%);
		left: calc((-1 * (100vw - 100%) / 2) + 15px);
		flex-direction: column;
	}
	.active {
		left: 12px;
		&::before {
			left: -12px;
			top: 50%;
			transform: translateY(-50%);
		}
	}
	.active {
		left: 10px;
		&::before {
			left: -10px;
			top: 50%;
			transform: translateY(-50%);
		}
	}
}
@media (max-width: 840px) {
	.active {
		top: 10px;
		&::before {
			top: -12px;
			left: 50%;
			transform: translateX(-50%);
		}
	}
}

@media (max-width: 840px) {
	.active {
		top: 10px;
		&::before {
			top: -10px;
			left: 50%;
			transform: translateX(-50%);
		}
	}
}
</style>
