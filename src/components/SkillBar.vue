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
	margin: 15px 0px;
}
.skillBar--single {
	height: 20px;
}
.light {
	.skillBar--chart {
		border: 1px solid #f8b526;
	}
	.skillBar--single {
		background: linear-gradient(to right, #f5cd77, #f8b526);
	}
}
.dark {
	.skillBar--chart {
		border: 1px solid #944bbe;
	}
	.skillBar--single {
		background: linear-gradient(to right, #a646dd, #944bbe);
	}
}
</style>
