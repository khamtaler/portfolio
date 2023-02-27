<template>
	<footer class="footer"></footer>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
.footer {
	position: absolute;
	height: 15px;
	width: 100vw;
	left: calc(-1 * (100vw - 100%) / 2);
	bottom: 0;
}
.light {
	.footer {
		background: #fe5209;
	}
}

.dark {
	.footer {
		background: #944bbe;
	}
}
</style>
