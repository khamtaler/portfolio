<template>
	<button class="button button--color" :class="colorClass" :title="title"></button>
</template>

<script>
export default {
	props: {
		colorClass: String,
		title: String,
	},
};
</script>

<style lang="scss" scoped>
.button--color {
	width: 20px;
	height: 20px;
	padding: 0px;
	border: 1px solid #fff;
}

.button--color---light {
	background-color: #a7a7a7;
}
.button--color---dark {
	background-color: #1f1f1f;
}
.button--color---colorful {
	background: linear-gradient(#e66465, #9198e5);
}

// @media (max-width: 840px) {
// 	.button--color {
// 		margin: 0px;
// 	}
// }
</style>
