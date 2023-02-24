<template>
	<div class="contact">
		<div class="contact--imageContainer hideMobile">
			<img class="contact--image" src="../assets/images/avatar.svg" alt="Creator picture" />
		</div>
		<div class="contact--formContainer">
			<h4 v-html="$t('contact-form-header')"></h4>
			<textarea
				class="contact--message"
				v-model="message"
				:placeholder="$t('contact-text-placeholder')"
			/>
			<input
				class="contact--email"
				v-model="email"
				:placeholder="$t('contact-email-placeholder')"
			/>
			<button
				type="button"
				class="button button--contact"
				@click="send()"
				@mouseover="textGo"
				@mouseleave="textReady"
			>
				{{ buttonText }}
			</button>
		</div>
	</div>
</template>

<script>
export default {
	data() {
		return {
			message: '',
			email: '',
			buttonText: 'Ready?',
		};
	},
	methods: {
		send() {
			alert(this.$t('contactAlert'));
		},
		textGo() {
			this.buttonText = 'Lets Go!';
		},
		textReady() {
			this.buttonText = 'Ready?';
		},
	},
};
</script>

<style lang="scss" scoped>
.contact {
	display: flex;
	align-items: center;
	justify-content: center;
	width: 100%;
	border-radius: 10px;
}

.contact {
	background: #fff;
	border-radius: 15px 0px 15px 0px;
	padding: 20px;
}

.contact::before,
.contact::after {
	content: '';
	background: transparent;
	height: 130px;
	width: 90px;
	position: absolute;
}
.contact::before {
	bottom: -5px;
	left: -5px;
}

.contact::after {
	top: -5px;
	right: -5px;
}
.contact--formContainer {
	display: flex;
	flex-direction: column;
	width: 100%;
	padding: 20px;
	gap: 15px;
}
.contact--image {
	display: block;
	width: 100%;
	max-width: 300px;
	margin: auto;
	border-radius: 50%;
}
.contact--formHeader {
	font-size: 1.2rem;
	color: #1f1f1f;
}
.contact--message:focus-visible,
.contact--email:focus-visible {
	outline: unset;
}
.contact--message,
.contact--email {
	padding: 10px;
	border-radius: 5px;
	border: 1px solid #1f1f1f;
}

.contact--message {
	min-height: 100px;
}
.button--contact {
	border: none;
	font-size: 18px;
	padding: 5px 20px;
	background: #fff;
}
.button--contact::before,
.button--contact::after {
	content: '';
	position: absolute;
	height: 100%;
	width: 100%;

	background: transparent;
	opacity: 0;
}
.button--contact::before {
	top: 0px;
	border-radius: 5px 0px 0px 0px;
}
.button--contact::after {
	bottom: 0px;
	border-radius: 0px 0px 5px 0px;
}
.button--contact:hover {
	background: transparent;
}
.button--contact::before {
	left: 0px;
}
.button--contact::after {
	right: 0px;
}
.button--contact:hover::before {
	left: -5px;
	top: -5px;
	opacity: 1;
}
.button--contact:hover::after {
	right: -5px;
	bottom: -5px;
	opacity: 1;
}

.light {
	.contact::before {
		border-left: 15px solid #f8b526;
		border-bottom: 15px solid #f8b526;
	}
	.contact::after {
		border-top: 15px solid #f8b526;
		border-right: 15px solid #f8b526;
	}

	.contact--message:focus-visible,
	.contact--email:focus-visible {
		border: 1px solid #f8b526;
		box-shadow: 0px 0px 5px 0px #f8b526;
	}
	.button--contact {
		box-shadow: 0px 0px 5px 0px #f8b526;
	}
	.button--contact:hover {
		box-shadow: none;
	}
	.button--contact::before {
		border-left: 2px solid #f8b526;
		border-top: 2px solid #f8b526;
	}
	.button--contact::after {
		border-right: 2px solid #f8b526;
		border-bottom: 2px solid #f8b526;
	}
}

.dark {
	.contact {
		background: #fff;
	}

	.contact::before {
		border-left: 15px solid #9e35db;
		border-bottom: 15px solid #9e35db;
	}
	.contact::after {
		border-top: 15px solid #9e35db;
		border-right: 15px solid #9e35db;
	}
	.button--contact {
		box-shadow: 0px 0px 5px 0px #d190f7;
	}
	.button--contact:hover {
		box-shadow: none;
	}
	.button--contact::before {
		border-left: 2px solid #d190f7;
		border-top: 2px solid #d190f7;
	}
	.button--contact::after {
		border-right: 2px solid #d190f7;
		border-bottom: 2px solid #d190f7;
	}
	.contact--message:focus-visible,
	.contact--email:focus-visible {
		border: 1px solid #944bbe;
		box-shadow: 0px 0px 5px 0px #944bbe;
	}
}

@media (min-width: 1200px) {
	.contact--imageContainer {
		width: 40%;
	}
	.contact--formContainer {
		width: 60%;
	}
}
@media (max-width: 1000px) {
	.contact--formHeader {
		font-size: 1rem;
	}
}
@media (min-width: 841px) {
	.contact {
		gap: 20px;
	}
}
</style>
