<script setup>
import TheMenu from './components/TheMenu.vue';
import TheAside from './components/TheAside.vue';
import TheFooter from './components/TheFooter.vue';
import BaseSection from './components/BaseSection.vue';
import BaseTile from './components/BaseTile.vue';
import TheAboutMe from './components/TheAboutMe.vue';
import TheContactForm from './components/TheContactForm.vue';
import ProjectTile from './components/ProjectTile.vue';
import TheSkills from './components/TheSkills.vue';
import PhoneIcon from './components/icons/PhoneIcon.vue';
import EnvelopeIcon from './components/icons/EnvelopeIcon.vue';
import GithubIcon from './components/icons/GithubIcon.vue';
import LinkedinIcon from './components/icons/LinkedinIcon.vue';
import CloseIcon from './components/icons/CloseIcon.vue';
import HamburgerIcon from './components/icons/HamburgerIcon.vue';
</script>

<template>
	<TheAside />
	<HamburgerIcon
		class="mobileMenuButton mobileMenuButton--open"
		@click="toggleMobileMenu"
	></HamburgerIcon>
	<CloseIcon
		class="mobileMenuButton mobileMenuButton--close"
		@click="toggleMobileMenu"
		:class="{ buttonVisible: mobile }"
	></CloseIcon>
	<TheMenu @changeTile="toggleTile" :class="{ mobile: mobile }"></TheMenu>

	<main class="main">
		<BaseTile v-if="show === `menu.home`" id="Homepage" class="homepage">
			<div class="homepage--section">
				<img
					class="homepage--section-avatar"
					src="./assets/images/avatar.svg"
					alt="Creator picture"
				/>
				<div class="homepage--section-desc">
					<h1 class="homepage--section-header">{{ $t('opening') }}</h1>
					<p class="homepage--section-text" v-html="$t('greetings')"></p>
				</div></div
		></BaseTile>
		<BaseTile v-if="show === `menu.about`" id="About" class="about"> <TheAboutMe /></BaseTile>
		<BaseTile v-if="show === `menu.projects`" id="Projects" class="projects">
			<ProjectTile
				:desc="$t('portfolio-vue')"
				link="#/"
				github="https://github.com/khamtaler/portfolio"
			>
				<img
					class="projectTile--image"
					src="./assets/images/Portfolio.webp"
					alt="project picture"
				/>
			</ProjectTile>
			<ProjectTile
				:desc="$t('quizz-react')"
				link="https://clever-khapse-9eeb96.netlify.app/"
				github="https://github.com/khamtaler/React_ts_quizz"
			>
				<img class="projectTile--image" src="./assets/images/Quizz.webp" alt="project picture" />
			</ProjectTile>

			<ProjectTile
				:desc="$t('landing-nuxt')"
				link="https://creative-souffle-842769.netlify.app/"
				github="https://github.com/khamtaler/nuxt_landing"
			>
				<img
					class="projectTile--image"
					src="./assets/images/ProductFactory.webp"
					alt="project picture"
				/>
			</ProjectTile>
			<ProjectTile
				:desc="$t('landing-vue')"
				link="https://sunny-mochi-22e9b8.netlify.app/"
				github="https://github.com/khamtaler/vue_landing"
			>
				<img class="projectTile--image" src="./assets/images/TuOglos.webp" alt="project picture" />
			</ProjectTile>
		</BaseTile>
		<BaseTile v-if="show === `menu.skills`" id="Skills" class="skills"> <TheSkills /></BaseTile>
		<BaseTile v-if="show === `menu.contact`" id="Contact" class="contact">
			<BaseSection class="contact--info">
				<div class="contact--info-links">
					<h2 class="contact--info-header">{{ $t('contactHeader') }}</h2>

					<a class="contact--info-link" href="mailto:tsroka41@gmail.com" target="blank"
						><EnvelopeIcon class="icon mediaIcon" /> tsroka41@gmail.com</a
					>
					<a class="contact--info-link" href="tel:+48794794818" target="blank">
						<PhoneIcon class="icon mediaIcon" /> 794 794 818</a
					>
					<a class="contact--info-link" href="https://github.com/khamtaler" target="blank">
						<GithubIcon class="icon mediaIcon" />Github</a
					>
					<a
						class="contact--info-link"
						href="https://www.linkedin.com/in/tomasz-sroka-114790243/"
						target="blank"
						><LinkedinIcon class="icon mediaIcon" />Linkedin</a
					>
				</div>
				<div class="contact--info-city">
					<p v-html="$t('livingPlace')"></p>
					<div class="contact--info-images">
						<img class="contact--info-image" src="./assets/images/Lake.webp" alt="Lake" />
						<img class="contact--info-image" src="./assets/images/Balon.webp" alt="Balon" />
						<img class="contact--info-image" src="./assets/images/Storm.webp" alt="Storm" />
					</div>
				</div>
			</BaseSection>
			<TheContactForm />
		</BaseTile>
	</main>
	<TheFooter />
</template>

<script>
export default {
	data() {
		return {
			show: 'menu.home',
			mobile: false,
		};
	},
	components: {
		TheMenu,
		TheAside,
		TheFooter,
		BaseSection,
		BaseTile,
		TheAboutMe,
		TheContactForm,
		ProjectTile,
		TheSkills,
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
	margin-top: 80px;
}
.homepage--section {
	display: flex;
}
.homepage--section-desc {
	background: #fff;
	border-radius: 15px 0px 15px 0px;
	padding: 20px;
}

.homepage--section-desc::before,
.homepage--section-desc::after {
	content: '';
	background: transparent;
	height: 130px;
	width: 90px;
	position: absolute;
}
.homepage--section-desc::before {
	bottom: -5px;
	left: -5px;
}

.homepage--section-desc::after {
	top: -5px;
	right: -5px;
}

.homepage--section-header {
	margin-bottom: 15px;
	transition: 0s;
}
.homepage--section-text {
	line-height: 2;
}

.homepage--section-avatar {
	border-radius: 50%;
	margin: auto;
	padding: 0px 60px 120px;
}
.contact--info {
	display: flex;
	width: 100%;
}
.contact--info-header {
	color: #272727;
	text-decoration: underline;
	margin-bottom: 15px;
}
.contact--info-links {
	display: flex;
	flex-direction: column;
	justify-content: space-around;
	padding: 0px 10px;
}
.mediaIcon {
	width: 16px;
	height: auto;
}
.contact--info-link {
	display: flex;
	align-items: center;
	gap: 6px;
	font-size: 18px;
	text-decoration: none;
	margin: 5px 0px;
	color: #471564;
}

.contact--info-city {
	padding: 0px 0px 0px 20px;
	margin-left: auto;
}
.contact--info-images {
	margin-top: 10px;
	display: flex;
	justify-content: space-between;
}
.contact--info-image {
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
.projectTile--image {
	display: block;
	margin: 0px;
	height: 205px;
	width: 100%;
	object-fit: cover;
	overflow: hidden;
	border-radius: 5px;
}

.projectTile:hover .projectTile--image {
	transform: scale(1.05);
}

.light {
	.homepage--section-desc {
		background: #fff;
		color: #272727;
		transition: 0ms;
	}

	.homepage--section-desc::before {
		border-left: 15px solid #f8b526;
		border-bottom: 15px solid #f8b526;
	}
	.homepage--section-desc::after {
		border-top: 15px solid #f8b526;
		border-right: 15px solid #f8b526;
	}

	.homepage--section-desc {
		border: 1px solid #272727;
	}

	.contact--info-link:hover {
		color: #f8b526;
	}
}
.dark {
	.mobileMenuButton {
		filter: invert(99%) sepia(0%) saturate(2%) hue-rotate(29deg) brightness(107%) contrast(100%);
	}

	.homepage--section-desc {
		background: #272727;
		color: #fff;
		transition: 0ms;
	}
	.homepage--section-desc::before {
		border-left: 15px solid #9e35db;
		border-bottom: 15px solid #9e35db;
	}
	.homepage--section-desc::after {
		border-top: 15px solid #9e35db;
		border-right: 15px solid #9e35db;
	}

	.contact--info-link:hover {
		color: #9e35db;
	}
	.contact--info {
		background: #272727;
		color: #fff;
	}
	.contact--info-header,
	.contact--info-link {
		color: #fff;
	}
	.mediaIcon {
		filter: invert(100%) sepia(72%) saturate(48%) hue-rotate(230deg) brightness(116%) contrast(100%);
	}
}

@media (min-width: 1200px) {
	.homepage--section-text {
		font-size: 1.1rem;
	}
}

@media (min-width: 841px) {
	.homepage--section-desc,
	.homepage--section-avatar {
		width: 50%;
	}
}

@media (max-width: 840px) {
	.mobileMenuButton {
		display: block;
		width: 25px;
		height: auto;
		position: absolute;
		left: 20px;
	}
	.mobileMenuButton:hover {
		cursor: pointer;
	}
	.mobileMenuButton--open {
		top: 20px;
	}
	.mobileMenuButton--close {
		top: 17px;
		display: none;
	}

	.buttonVisible {
		display: block;
		z-index: 5;
	}
	.main {
		margin-top: 50px;
	}

	.homepage--section-avatar {
		padding: 0px 60px 30px;
	}
	.contact--info {
		flex-direction: column;
	}
	.contact {
		gap: 20px;
	}
	.contact--info-links {
		padding: 0px;
	}
	.contact--info-link {
		font-size: 1rem;
		margin-bottom: 10px;
	}
	.contact--info-city {
		padding: 0;
	}
	.projectTile--image {
		aspect-ratio: 1;
		height: unset;
		margin-bottom: 15px;
	}
	.homepage--section-avatar {
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

@media (min-width: 601px) {
	.tile.projects {
		flex-direction: row;
		flex-wrap: wrap;
	}
}
@media (max-width: 600px) {
	.projects {
		flex-direction: column;
	}
}
</style>
