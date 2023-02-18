<template>
	<div class="menu">
		<MenuItem v-for="tab in tabs" @click="$emit('changeTile', tab)" :key="tab">{{ tab }}</MenuItem>
	</div>
</template>

<script>
import MenuItem from './MenuItem.vue';
export default {
	data() {
		return {
			tabs: ['Home', 'About me', 'Projects', 'Skills', 'Contact'],
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
	justify-content: end;
	gap: 50px;
	margin-bottom: 30px;
	padding: 10px 0px;
}
</style>
