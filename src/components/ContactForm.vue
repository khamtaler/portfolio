<template>
	<div class="contact">
		<div class="contact--imageContainer">
			<img class="contact--image" src="../assets/images/avatar.jpg" />
		</div>
		<div class="contact--formContainer">
			<h4 class="contact--formHeader">
				Do You need any further information? <br />

				Write your message bellow and send it directly to me &#128512;
			</h4>
			<textarea class="contact--message" v-model="message" placeholder="input your message" />
			<input class="contact--email" v-model="email" placeholder="Your email" />
			<button
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
			this.buttonText = 'Go!';
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
	background: #fff;
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
	width: 100px;
}
.dark {
	.contact {
		box-shadow: 0px 0px 40px 10px rgb(41, 146, 207);
	}
	.button--contact {
		box-shadow: 0px 0px 10px 0px rgb(41, 146, 207);
	}
	.button--contact:hover {
		box-shadow: 0px 0px 20px 0px rgb(41, 146, 207);
	}
	.contact--message:focus-visible,
	.contact--email:focus-visible {
		border: 1px solid rgb(41, 146, 207);
		box-shadow: 0px 0px 5px 0px rgb(41, 146, 207);
	}
	.contact--email {
		border: 1px solid rgb(41, 146, 207);
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
</style>
