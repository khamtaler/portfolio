<template>
	<p>
		<b>{{ name }}</b>
	</p>
	<div class="skillBar">
		<slot />
		<div class="skillBar--chart">
			<div class="skillBar--single" :style="style"></div>
		</div>
	</div>
</template>

<script>
export default {
	props: {
		width: String,
		name: String,
	},
	computed: {
		style() {
			return 'width: ' + this.width + '%';
		},
	},
};
</script>

<style lang="scss" scoped>
.skillBar {
	display: flex;
	align-items: center;
	gap: 20px;
}
.skillBar--chart {
	width: 100%;
	border-radius: 5px;
	border: 1px solid #944bbe;
	margin: 15px 0px;
}
.skillBar--single {
	height: 20px;
	background: linear-gradient(to right, #a646dd, #944bbe);
}
</style>
