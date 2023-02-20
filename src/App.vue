<script setup>
import Menu from './components/Menu.vue';
import ColorsAside from './components/ColorsAside.vue';
import Section from './components/Section.vue';
import Tile from './components/Tile.vue';
import Tabs from './components/Tabs.vue';
import ContactForm from './components/ContactForm.vue';
import ProjectTile from './components/ProjectTile.vue';
import Skills from './components/Skills.vue';
import PhoneIcon from './components/icons/PhoneIcon.vue';
import EnvelopeIcon from './components/icons/EnvelopeIcon.vue';
import GithubIcon from './components/icons/GithubIcon.vue';
import LinkedinIcon from './components/icons/LinkedinIcon.vue';
import CloseIcon from './components/icons/CloseIcon.vue';
import HamburgerIcon from './components/icons/HamburgerIcon.vue';
</script>

<template>
	<ColorsAside />
	<HamburgerIcon
		class="mobileMenuButton mobileMenuButton--open"
		@click="toggleMobileMenu"
	></HamburgerIcon>
	<CloseIcon
		class="mobileMenuButton mobileMenuButton--close"
		@click="toggleMobileMenu"
		:class="{ buttonVisible: mobile }"
	></CloseIcon>
	<Menu @changeTile="toggleTile" :class="{ mobile: mobile }"></Menu>

	<main class="main">
		<Tile v-if="show === `Home`" id="Homepage" class="homepage">
			<div class="homepage--section">
				<img
					class="homepage--sectionImage"
					src="./assets/images/avatar.jpg"
					alt="Creator picture"
				/>
				<div class="homepage--sectionText">
					<h1>{{ $t('opening') }}</h1>
					<p class="homepage--sectionTextWelcome" v-html="$t('greetings')"></p>
				</div></div
		></Tile>
		<Tile v-if="show === `About me`" id="About" class="about"> <Tabs /></Tile>
		<Tile v-if="show === `Projects`" id="Projects" class="projects">
			<ProjectTile
				desc="Portfolio in Vue.js"
				link="#/"
				github="https://github.com/khamtaler/portfolio"
			>
				<img class="projects--image" src="./assets/images/Portfolio.webp" alt="project picture" />
			</ProjectTile>
			<ProjectTile
				desc="Quizz in React"
				link="https://clever-khapse-9eeb96.netlify.app/"
				github="https://github.com/khamtaler/React_ts_quizz"
			>
				<img class="projects--image" src="./assets/images/Quizz.webp" alt="project picture" />
			</ProjectTile>

			<ProjectTile
				desc="Landing in Nuxt.js"
				link="https://creative-souffle-842769.netlify.app/"
				github="https://github.com/khamtaler/nuxt_landing"
			>
				<img
					class="projects--image"
					src="./assets/images/ProductFactory.webp"
					alt="project picture"
				/>
			</ProjectTile>
			<ProjectTile
				desc="Landing in Vue.js"
				link="https://sunny-mochi-22e9b8.netlify.app/"
				github="https://github.com/khamtaler/vue_landing"
			>
				<img class="projects--image" src="./assets/images/TuOglos.webp" alt="project picture" />
			</ProjectTile>
		</Tile>
		<Tile v-if="show === `Skills`" id="Skills" class="skills"> <Skills /></Tile>
		<Tile v-if="show === `Contact`" id="Contact" class="contact">
			<Section class="section--contact">
				<div class="contact--information">
					<h2 class="contact--header">{{ $t('contactHeader') }}</h2>

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
						<img class="contact--image" src="./assets/images/Lake.webp" alt="Lake" />
						<img class="contact--image" src="./assets/images/Balon.webp" alt="Balon" />
						<img class="contact--image" src="./assets/images/Storm.webp" alt="Storm" />
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
			mobile: false,
		};
	},
	components: {
		Menu,
		ColorsAside,
		Section,
		Tile,
		Tabs,
		ContactForm,
		ProjectTile,
		Skills,
		PhoneIcon,
		EnvelopeIcon,
		GithubIcon,
		LinkedinIcon,
		CloseIcon,
		HamburgerIcon,
	},
	methods: {
		toggleTile(tile) {
			this.show = tile;
			console.log(window.innerWidth);
			if (window.innerWidth <= 840) {
				this.mobile = !this.mobile;
			}
		},
		toggleMobileMenu() {
			this.mobile = !this.mobile;
		},
	},
};
</script>

<style lang="scss" scoped>
.mobileMenuButton {
	display: none;
}

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
.homepage--sectionTextWelcome {
	line-height: 2;
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

.light {
}
.dark {
	.mobileMenuButton {
		filter: invert(99%) sepia(0%) saturate(2%) hue-rotate(29deg) brightness(107%) contrast(100%);
	}
}

@media (min-width: 841px) {
	.homepage--sectionText,
	.homepage--sectionImage {
		width: 50%;
	}
}

@media (min-width: 601px) {
	.projects {
		flex-direction: row;
		flex-wrap: wrap;
	}
}
@media (max-width: 600px) {
	.projects {
		flex-direction: column;
	}
}
@media (max-width: 840px) {
	.mobileMenuButton {
		display: block;
		width: 25px;
		height: auto;
		position: absolute;
		left: 10px;
	}
	.mobileMenuButton:hover {
		cursor: pointer;
	}
	.mobileMenuButton--open {
		top: 15px;
	}
	.mobileMenuButton--close {
		top: 12px;
		display: none;
	}

	.buttonVisible {
		display: block;
		z-index: 5;
	}
	.main {
		margin-top: 50px;
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
