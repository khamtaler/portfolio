<template>
	<div class="menuItem">
		<button class="button menuItem--button">
			<slot />
		</button>
	</div>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
.menuItem--button {
	background: transparent;
	color: #fff;
	border-radius: 0px;
	text-align: center;
	border: none;
	opacity: 0.9;
}

.menuItem--button::before {
	content: '';
	position: absolute;
	bottom: 0px;
	left: 0px;
	width: 100%;
	height: 2px;
	background: #fff;
}
.menuItem--button:hover {
	margin-bottom: 5px;
	text-shadow: 0px 1px #fff;
	opacity: 1;
}
.menuItem--button:hover::before {
	box-shadow: 0px 0px 1px 1px #fff;
}
.light {
	.menuItem--button {
		color: #000;
	}
	.menuItem--button::before {
		background: #000;
	}
}
</style>
