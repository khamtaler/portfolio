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
	justify-content: space-between;
	max-width: 80vw;
	width: 100%;
	max-height: 80vh;
	height: 100%;
	background: #fff;
	padding: 20px;
	border-radius: 10px;
}
</style>
