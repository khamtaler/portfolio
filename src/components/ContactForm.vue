<template>
	<div class="contact">
		<div class="contact--imageContainer hideMobile">
			<img class="contact--image" src="../assets/images/avatar.jpg" alt="Creator picture" />
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
			console.log(this.message);
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
	// width: 100px;
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
	width: 1px;
	background: #1f1f1f;
	opacity: 0;
	top: 0px;
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
	opacity: 1;
}
.button--contact:hover::after {
	right: -5px;
	opacity: 1;
}

.dark {
	.button--contact {
		box-shadow: 0px 0px 5px 0px #944bbe;
	}
	.button--contact:hover {
		box-shadow: none;
	}
	.button--contact::before,
	.button--contact::after {
		background: #944bbe;
		box-shadow: 0px 0px 1px 1px #944bbe;
	}
	.contact--message:focus-visible,
	.contact--email:focus-visible {
		border: 1px solid #944bbe;
		box-shadow: 0px 0px 5px 0px #944bbe;
	}
	.contact--email {
		border: 1px solid #944bbe;
	}
	.contact {
		background: #fff;
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
