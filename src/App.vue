<script setup>
import Menu from './components/Menu.vue';
import ColorsAside from './components/ColorsAside.vue';
import Section from './components/Section.vue';
import Tile from './components/Tile.vue';
import Tabs from './components/Tabs.vue';
import ContactForm from './components/ContactForm.vue';
import ProjectTile from './components/ProjectTile.vue';
import PhoneIcon from './components/icons/PhoneIcon.vue';
import EnvelopeIcon from './components/icons/EnvelopeIcon.vue';
import GithubIcon from './components/icons/GithubIcon.vue';
import LinkedinIcon from './components/icons/LinkedinIcon.vue';
import Skills from './components/Skills.vue';
</script>

<template>
	<ColorsAside />
	<Menu @changeTile="toggleTile"></Menu>
	<main class="main">
		<Tile v-if="show === `Home`" id="Homepage" class="homepage">
			<div class="homepage--section">
				<img class="homepage--sectionImage" src="./assets/images/avatar.jpg" />
				<div class="homepage--sectionText">
					<h2>Welcome!</h2>
					<p>
						My name is <b>Tomasz Sroka</b> and this is my website. The idea behind the project was
						to make a simple single page website I could describe myself on. You can toggle
						different colors in left menu if You wish. Projects are available to be viewed in
						projects tab. You can contact me via links included in contact tab. Enjoy your stay
						&#128512;
					</p>
				</div>
			</div></Tile
		>
		<Tile v-if="show === `About me`" id="About" class="about"> <Tabs /></Tile>
		<Tile v-if="show === `Projects`" id="Projects" class="projects">
			<ProjectTile
				desc="Quizz in React"
				link="https://clever-khapse-9eeb96.netlify.app/"
				github="https://github.com/khamtaler/React_ts_quizz"
			>
				<img class="projects--image" src="./assets/images/Quizz.webp" />
			</ProjectTile>

			<ProjectTile
				desc="Landing in Nuxt.js"
				link="https://creative-souffle-842769.netlify.app/"
				github="https://github.com/khamtaler/nuxt_landing"
			>
				<img class="projects--image" src="./assets/images/ProductFactory.webp" />
			</ProjectTile>
			<ProjectTile
				desc="Landing in Vue.js"
				link="https://sunny-mochi-22e9b8.netlify.app/"
				github="https://github.com/khamtaler/vue_landing"
			>
				<img class="projects--image" src="./assets/images/TuOglos.webp" />
			</ProjectTile>
			<ProjectTile desc="Ecocalculator in Vanilla JS" link="https://lively.pl/ekokalkulator/">
				<img class="projects--image" src="./assets/images/Kalkulator.webp" />
			</ProjectTile>
		</Tile>
		<Tile v-if="show === `Skills`" id="Skills" class="skills"> <Skills /></Tile>
		<Tile v-if="show === `Contact`" id="Contact" class="contact">
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
	data() {
		return {
			show: 'Home',
		};
	},
	components: {
		Menu,
		Section,
		ContactForm,
		ColorsAside,
		ProjectTile,
		Tabs,
		Skills,
	},
	methods: {
		toggleTile(tile) {
			this.show = tile;
		},
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
.homepage--section {
	display: flex;
}
.homepage--sectionText {
	background: #fff;
	border-radius: 10px;
	padding: 20px;
}

.homepage--sectionImage {
	mix-blend-mode: multiply;
}
.section--contact {
	display: flex;
	width: 100%;
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
	height: auto;
}
.contact--link {
	display: flex;
	align-items: center;
	gap: 6px;
	font-size: 18px;
	text-decoration: none;
	margin: 5px 0px;
	color: #2e2d2d;
}

.contact--city {
	padding: 0px 0px 0px 20px;
	margin-left: auto;
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
.projects {
	flex-direction: row;
	align-items: center;
	justify-content: space-around;
	gap: 20px;
	flex-wrap: wrap;
}
.projects--image {
	height: 200px;
	width: 100%;
	object-fit: cover;
	overflow: hidden;
	border-radius: 5px;
	transition: 1s;
}
.projects--image:hover {
	transform: scale(1.05);
}
@media (min-width: 801px) {
	.homepage--sectionText,
	.homepage--sectionImage {
		width: 50%;
	}
}
@media (max-width: 800px) {
	.projects {
		flex-direction: column;
	}
	.section--contact {
		flex-direction: column;
	}
	.contact {
		gap: 20px;
	}
	.contact--information {
		padding: 0px;
	}
	.contact--link {
		font-size: 1rem;
		margin-bottom: 10px;
	}
	.contact--city {
		padding: 0;
	}
	.projects--image {
		aspect-ratio: 1;
		height: unset;
		margin-bottom: 15px;
	}
	.homepage--sectionImage {
		width: 100%;
	}
	.homepage--section {
		flex-direction: column;
		justify-content: center;
		align-items: center;
		width: 100%;
		padding: 20px;
	}
}
</style>
