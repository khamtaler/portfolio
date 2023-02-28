<template>
	<div class="tab--content">
		<slot />
	</div>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
.tab--content {
	width: 100%;
	margin: 30px 0px;
	padding: 10px 30px;
	border-radius: 10px;
	border: none;
}

.light {
	.tab--content {
		background: #fff;
		color: #272727;
	}
}
.dark {
	.tab--content {
		background: #272727;
		color: #fff;
	}
}
</style>
