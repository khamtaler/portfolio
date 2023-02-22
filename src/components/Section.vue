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
	background: #fff;
	padding: 20px;
	border-radius: 10px;
	border: 1px solid #1f1f1f;
}
.light {
	.section {
		border: 1px solid #1f1f1f;
	}
}
</style>
