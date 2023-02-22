<template>
	<div class="menuItem">
		<button type="button" class="button menuItem--button">
			<slot />
		</button>
	</div>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
.menu:not(.mobile) .menuItem:last-child {
	margin-right: 30px;
}
.menuItem--button {
	background: transparent;
	color: #fff;
	font-weight: 700;
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
	transform: translateY(-6px);
	opacity: 1;
	transition: 0.5s ease-in-out;
}
.menuItem--button:hover::before {
	box-shadow: 0px 0px 1px 1px #fff;
}

.menuItem--button {
	color: #fff;
}
.menuItem--button::before {
	background: #fff;
}

.mobile {
	.menuItem--button {
		font-size: 20px;
	}
}
.light {
	.menuItem--button {
		color: #fff;
	}
	.active {
		.menuItem--button::before {
			background: #ffde0b;
			box-shadow: 0px 0px 1px 1px #ffde0b;
		}
	}
}

.dark {
	.active {
		.menuItem--button::before {
			background: #a7a7a7;
			box-shadow: 0px 0px 1px 1px #a7a7a7;
		}
	}
}
</style>
