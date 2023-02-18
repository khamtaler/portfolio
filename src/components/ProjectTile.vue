<script setup>
import GithubIcon from './icons/GithubIcon.vue';
</script>

<template>
	<div class="projectTile">
		<a :href="link" target="blank">
			<slot />
			<p class="projectTile--desc">{{ desc }}</p>
		</a>
		<a class="projectTile--github" :href="github" target="blank">
			<GithubIcon class="githubIcon" /> Github</a
		>
	</div>
</template>

<script>
export default {
	props: {
		desc: String,
		link: String,
		github: String,
	},
	components: {
		GithubIcon,
	},
};
</script>

<style lang="scss" scoped>
.projectTile {
	width: 30%;
}
.projectTile--desc {
	font-size: 18px;
	text-align: center;
}
.projectTile--github {
	display: block;
	text-align: center;
}
.githubIcon {
	width: 16px;
}
.dark {
	.projectTile--github {
		margin-top: 5px;
		color: #471564;
	}
	.projectTile::before {
		content: '';
		position: absolute;
		bottom: -5px;
		width: 100%;
		height: 1px;
		background: #471564;
		box-shadow: 0px 0px 3px 1px #471564;
	}
}
</style>
