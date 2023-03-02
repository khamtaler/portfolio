<template>
	<div class="skillbar">
		<h4 class="skillbar--header">
			<b>{{ name }}</b>
		</h4>
		<div class="skillbar--bar">
			<slot />
			<div class="skillbar--bar-chart">
				<div class="skillbar--bar-line" :style="style"></div>
			</div>
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
.skillbar--bar {
	display: flex;
	align-items: center;
	gap: 20px;
}
.skillbar--bar-chart {
	width: 100%;
	border-radius: 5px;
	margin: 15px 0px;
}
.skillbar--bar-line {
	height: 20px;
}
.light {
	.skillbar--header {
		color: #272727;
	}
	.skillbar--bar-chart {
		border: 1px solid #f8b526;
	}
	.skillbar--bar-line {
		background: linear-gradient(to right, #f5cd77, #f8b526);
	}
}
.dark {
	.skillbar--header {
		color: #fff;
	}
	.skillbar--bar-chart {
		border: 1px solid #944bbe;
	}
	.skillbar--bar-line {
		background: linear-gradient(to right, #a646dd, #944bbe);
	}
}
</style>
