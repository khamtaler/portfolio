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
	background: transparent;
	padding: 10px;
	border-radius: 10px;
}

@media (max-width: 840px) {
	.tile {
		padding: 20px 15px;
		max-width: 100%;
	}
}
</style>
