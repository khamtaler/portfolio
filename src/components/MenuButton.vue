<template>
	<div class="menuButton">
		<button type="button" class="button menuButton--button">
			<slot />
		</button>
	</div>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
.menu:not(.mobile) .menuButton:last-child {
	margin-right: 30px;
}
.menuButton--button {
	background: transparent;
	color: #fff;
	font-weight: 700;
	border-radius: 0px;
	text-align: center;
	border: none;
	opacity: 0.9;
}

.menuButton--button::before {
	content: '';
	position: absolute;
	bottom: 0px;
	left: 0px;
	width: 100%;
	height: 2px;
	background: #fff;
}
.menuButton--button:hover {
	transform: translateY(-6px);
	opacity: 1;
	transition: 0.5s ease-in-out;
}
.menuButton--button:hover::before {
	box-shadow: 0px 0px 1px 1px #fff;
}

.menuButton--button {
	color: #fff;
}
.menuButton--button::before {
	background: #fff;
}
.active {
	.menuButton--button {
		opacity: 1;
	}
}

.mobile {
	.menuButton--button {
		font-size: 20px;
	}
}
.light {
	.mobile {
		.menuButton--button {
			color: #000;
		}
	}
	.active {
		.menuButton--button::before {
			background: #ffde0b;
			box-shadow: 0px 0px 1px 1px #ffde0b;
		}
	}
}

.dark {
	.active {
		.menuButton--button {
			color: #9e35db;
		}
		.menuButton--button::before {
			background: #9e35db;
			box-shadow: 0px 0px 1px 1px #9e35db;
		}
	}
}

@media (min-width: 1200px) {
	.menuButton--button {
		font-size: 1.1rem;
	}
}
</style>
