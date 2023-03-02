<template>
	<div class="section">
		<slot />
	</div>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
.section {
	padding: 20px;
	border-radius: 10px;
}
.light {
	.section {
		background: #fff;
		border: 1px solid #272727;
	}
}
</style>
