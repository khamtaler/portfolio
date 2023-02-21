<template>
	<div class="menu">
		<MenuItem
			:class="{ active: active === tab.text_key }"
			v-for="tab in tabs"
			@click="$emit('changeTile', tab.text_key), (active = tab.text_key)"
			:key="tab.text_key"
			>{{ $t(tab.text_key) }}</MenuItem
		>
	</div>
</template>

<script>
import MenuItem from './MenuItem.vue';
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
		MenuItem,
	},
};
</script>

<style lang="scss" scoped>
.menu {
	display: flex;
	flex-direction: row;
	width: 100%;
	min-height: 62px;
	align-items: end;
	justify-content: flex-end;
	gap: 50px;
	margin-bottom: 30px;
	padding: 10px 0px;
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
