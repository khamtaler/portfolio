<template>
	<div class="tabItem">
		<slot />
	</div>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
.tabItem {
	background-color: #fff;
	padding: 10px;
	margin: 10px 0px;
	border-radius: 10px;
}
.light {
	.tabItem {
		background-color: #fff;
		padding: 10px;
		margin: 10px 0px;
		border-radius: 10px;
		border: 1px solid #000;
	}
}
</style>
