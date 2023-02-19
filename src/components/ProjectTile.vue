<script setup>
import GithubIcon from './icons/GithubIcon.vue';
</script>

<template>
	<div class="projectTile">
		<a :href="link" target="blank">
			<slot />
			<p class="projectTile--desc">{{ desc }}</p>
		</a>
		<a
			class="projectTile--github"
			:class="{ crossed: !github, disabled: !github }"
			:href="{ github }"
			target="blank"
		>
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
.projectTile::before {
	content: '';
	position: absolute;
	bottom: -5px;
	width: 100%;
	height: 1px;
}
.crossed {
	text-decoration: line-through;
}
.disabled {
	pointer-events: none;
	opacity: 0.5;
}
.dark {
	.projectTile--github {
		margin-top: 5px;
		color: #471564;
	}
	.projectTile::before {
		background: #471564;
		box-shadow: 0px 0px 3px 1px #471564;
	}
}

@media (min-width: 841px) {
	.projectTile {
		width: 30%;
	}
}
@media (min-width: 601px) and (max-width: 840px) {
	.projectTile {
		width: 45%;
	}
}
@media (max-width: 840px) {
	.projectTile {
		margin-bottom: 10px;
	}
}
</style>
