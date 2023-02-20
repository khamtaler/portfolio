<template>
	<div class="menu">
		<MenuItem
			:class="{ active: active === tab }"
			v-for="tab in tabs"
			@click="$emit('changeTile', tab), (active = tab)"
			:key="tab"
			>{{ tab }}</MenuItem
		>
	</div>
</template>

<script>
import MenuItem from './MenuItem.vue';
export default {
	data() {
		return {
			tabs: ['Home', 'About me', 'Projects', 'Skills', 'Contact'],
			active: 'Home',
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
	align-items: center;
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

		z-index: 2;
		position: absolute;
		height: 100vh;
		width: 100vw;
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
