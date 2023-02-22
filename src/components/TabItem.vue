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
	width: 100%;
	background-color: #fff;
	padding: 10px 30px;
	margin: 30px 0px;
	border-radius: 10px;
	border: none;
}
.tabItem--borders::before,
.tabItem--borders::after {
	content: '';
	position: absolute;
	width: 20px;
	height: 110%;
	background: transparent;
}
.tabItem--borders::before {
	left: -5px;
	top: -5%;
}
.tabItem--borders::after {
	right: -5px;
	top: -5%;
}
.light {
	.tabItem--borders::before {
		border-top: 10px solid #f8b526;
		border-bottom: 10px solid #f8b526;
		border-left: 10px solid #f8b526;
	}
	.tabItem--borders::after {
		border-top: 10px solid #f8b526;
		border-right: 10px solid #f8b526;
		border-bottom: 10px solid #f8b526;
	}
}
.dark {
	.tabItem--borders::before {
		border-top: 10px solid #944bbe;
		border-bottom: 10px solid #944bbe;
		border-left: 10px solid #944bbe;
	}
	.tabItem--borders::after {
		border-top: 10px solid #944bbe;
		border-right: 10px solid #944bbe;
		border-bottom: 10px solid #944bbe;
	}
}
</style>
