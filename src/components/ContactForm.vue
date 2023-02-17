<template>
	<div class="contact">
		<div class="contact--imageContainer">
			<img class="contact--image" src="#/" />
		</div>
		<div class="contact--formContainer">
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
.contact--message {
	min-height: 100px;
}

.button--contact {
	width: 100px;
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
