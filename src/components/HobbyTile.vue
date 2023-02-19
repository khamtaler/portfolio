<template>
	<div class="hobbyTile">
		<slot />
		<p class="hobbyTile--desc">
			<b>{{ title }}</b>
		</p>
	</div>
</template>

<script>
export default {
	props: {
		title: String,
		required: true,
	},
};
</script>

<style lang="scss" scoped>
.hobbyTile--desc {
	text-align: center;
}
@media (min-width: 841px) {
	.hobbyTile {
		width: 30%;
	}
}
</style>
