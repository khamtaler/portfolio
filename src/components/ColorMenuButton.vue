<template>
	<button type="button" class="button button--color" :class="setMode" :title="title"></button>
</template>

<script>
export default {
	props: {
		title: { type: String, required: true },
	},
	computed: {
		setMode() {
			return `button--color---${this.title}`;
		},
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
	background-color: #272727;
}
</style>
