<template>
	<div class="tile">
		<slot />
	</div>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
.tile {
	display: flex;
	flex-direction: column;
	align-items: center;
	justify-content: space-around;
	max-width: 80vw;
	width: 100%;
	height: 100%;
	min-height: 78vh;

	padding: 20px;
	border-radius: 10px;
}
.dark {
	.tile {
		background: #d1d0d0;
	}
}
</style>
