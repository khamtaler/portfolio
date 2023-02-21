<script setup>
import GithubIcon from './icons/GithubIcon.vue';
</script>

<template>
	<div class="projectTile">
		<a :href="link" target="_blank">
			<slot />
			<p class="projectTile--desc">{{ desc }}</p>
		</a>
		<div class="projectTile--githubContainer">
			<a
				class="projectTile--githubLink"
				:class="{ crossed: !github, disabled: !github }"
				:href="github"
				target="_blank"
			>
				<GithubIcon class="githubIcon" /> Github</a
			>
		</div>
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
	margin-top: 5px;
}
.projectTile--githubLink {
	display: flex;
	text-align: center;
	align-items: center;
	justify-content: center;
	margin-top: 5px;
	font-size: 20px;
	height: 30px;
	color: #1f1f1f;
}
.githubIcon {
	width: 16px;
	margin-right: 5px;
}
.projectTile::before {
	content: '';
	position: absolute;
	bottom: -15px;
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
.projectTile--githubContainer {
	display: flex;
	align-items: center;
	justify-content: center;
}
.projectTile--githubLink::after,
.projectTile--githubLink::before {
	position: absolute;
	opacity: 0;
	color: #1f1f1f;
}
.projectTile--githubLink::after {
	content: ']';
	right: 0px;
}
.projectTile--githubLink::before {
	content: '[';
	left: 0px;
}
.projectTile--githubLink:hover::after {
	right: -15px;
	opacity: 1;
}
.projectTile--githubLink:hover::before {
	left: -15px;
	opacity: 1;
}
.light {
	.projectTile--desc {
		color: #1f1f1f;
	}
	.projectTile::before {
		background: #1f1f1f;
		box-shadow: 0px 0px 3px 1px #1f1f1f;
	}
}
.dark {
	.projectTile--githubLink:hover {
		color: #944bbe;
	}
	.projectTile--githubLink:hover::before,
	.projectTile--githubLink:hover::after {
		color: #944bbe;
	}
	.projectTile::before {
		background: #944bbe;
		box-shadow: 0px 0px 3px 1px #944bbe;
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
