<script setup>
import Menu from './components/Menu.vue';
import ColorsAside from './components/ColorsAside.vue';
import Section from './components/Section.vue';
import Tile from './components/Tile.vue';
import ContactForm from './components/ContactForm.vue';
import PhoneIcon from './components/icons/PhoneIcon.vue';
import EnvelopeIcon from './components/icons/EnvelopeIcon.vue';
import GithubIcon from './components/icons/GithubIcon.vue';
import LinkedinIcon from './components/icons/LinkedinIcon.vue';
</script>

<template>
	<ColorsAside />
	<Menu />
	<main class="main">
		<Tile id="Contact" class="contact">
			<Section class="section--contact">
				<div class="contact--information">
					<h2 class="contact--header">Contact information:</h2>

					<a class="contact--link" href="mailto:tsroka41@gmail.com" target="blank"
						><EnvelopeIcon class="mediaIcon" /> tsroka41@gmail.com</a
					>
					<a class="contact--link" href="tel:+48794794818" target="blank">
						<PhoneIcon class="mediaIcon" /> 794 794 818</a
					>
					<a class="contact--link" href="https://github.com/khamtaler" target="blank">
						<GithubIcon class="mediaIcon" />Github</a
					>
					<a
						class="contact--link"
						href="https://www.linkedin.com/in/tomasz-sroka-114790243/"
						target="blank"
						><LinkedinIcon class="mediaIcon" />Linkedin</a
					>
				</div>
				<div class="contact--city">
					<p>Currently living in: <b>Cracow</b></p>
					<div class="contact--cityImages">
						<img class="contact--image" src="./assets/images/Lake.webp" />
						<img class="contact--image" src="./assets/images/Balon.webp" />
						<img class="contact--image" src="./assets/images/Storm.webp" />
					</div>
				</div>
			</Section>
			<ContactForm />
		</Tile>
	</main>
</template>

<script>
export default {
	components: {
		Menu,
		Section,
		ContactForm,
		ColorsAside,
	},
};
</script>

<style lang="scss" scoped>
.main {
	display: flex;
	align-items: center;
	justify-content: center;
	height: 100%;
	width: 100%;
}
.section--contact {
	display: flex;
	width: 100%;
	margin-bottom: 50px;
}
.contact--header {
	color: #1f1f1f;
	text-decoration: underline;
	margin-bottom: 15px;
}
.contact--information {
	display: flex;
	flex-direction: column;
	justify-content: space-around;
	padding: 0px 10px;
}
.mediaIcon {
	width: 16px;
}
.contact--link {
	display: flex;
	gap: 6px;
	font-size: 18px;
	text-decoration: none;
	margin: 5px 0px;
	color: #2e2d2d;
}

.contact--city {
	padding: 0px 0px 0px 20px;
	margin: auto;
}
.contact--cityImages {
	margin-top: 10px;
	display: flex;
	justify-content: space-between;
}
.contact--image {
	max-width: 30%;
	width: 100%;
	max-height: 200px;
	height: auto;
	border-radius: 10px;
	object-fit: cover;
}
</style>
