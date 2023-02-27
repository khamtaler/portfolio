<script setup>
import MenuButton from './MenuButton.vue';
</script>

<template>
	<div class="menu">
		<MenuButton
			:class="{ active: active === tab.text_key }"
			v-for="tab in tabs"
			@click="$emit('changeTile', tab.text_key), (active = tab.text_key)"
			:key="tab.text_key"
			>{{ $t(tab.text_key) }}</MenuButton
		>
	</div>
</template>

<script>
export default {
	data() {
		return {
			tabs: [
				{ text_key: 'menu.home' },
				{ text_key: 'menu.about' },
				{ text_key: 'menu.projects' },
				{ text_key: 'menu.skills' },
				{ text_key: 'menu.contact' },
			],
			active: 'menu.home',
		};
	},
	components: {
		MenuButton,
	},
};
</script>

<style lang="scss" scoped>
.menu {
	display: flex;
	position: absolute;
	flex-direction: row;
	width: 100vw;
	top: 0;
	right: calc(-1 * (100vw - 100%) / 2);
	min-height: 62px;
	height: 300px;
	align-items: baseline;
	justify-content: flex-end;
	gap: 50px;
	padding: 10px 0px;
	background-repeat: no-repeat;
	background-size: cover;
	transition: 0s;
}

.light {
	.menu {
		background-image: url('../assets/bgImages/MenuBackgroundLight.svg');
	}
}
.dark {
	.menu {
		background-image: url('../assets/bgImages/MenuBackgroundDark.svg');
	}
}
@media (max-width: 840px) {
	.menu {
		display: none;
	}
	.mobile {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		z-index: 2;
		position: absolute;
		height: 100vh;
		width: 100%;
		top: 0;
		bottom: 0;
		left: 0;
		right: 0;
	}
	.light {
		.mobile {
			background: #fff;
		}
	}
	.dark {
		.mobile {
			background: #000;
		}
	}
}
</style>
