<script setup>
import GithubIcon from './icons/GithubIcon.vue';
import FollowIcon from './icons/FollowIcon.vue';
</script>

<template>
	<div>
		<a class="projectTile--link" :href="link" target="_blank">
			<slot />
			<div class="projectTile--overlay">
				<p class="projectTile--overlayDesc">
					{{ $t('project-link') }} <FollowIcon class="icon followIcon" />
				</p>
			</div>
		</a>
		<p class="projectTile--desc">{{ desc }}</p>
		<div class="projectTile--githubContainer">
			<a
				class="projectTile--githubLink"
				:class="{ githubDisabled: !github }"
				:href="github"
				target="_blank"
			>
				<GithubIcon class="icon githubIcon" /> Github</a
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
		FollowIcon,
	},
};
</script>

<style lang="scss" scoped>
.projectTile--link {
	height: 100%;
	display: block;
}
.projectTile--overlay {
	display: flex;
	position: absolute;
	height: 100%;
	width: 100%;
	top: 0;
	opacity: 0;
	border-radius: 5px;
}
.projectTile--overlayDesc {
	font-size: 26px;
	text-align: center;
	margin: auto;
	font-weight: 700;
}
.projectTile--overlayDesc {
	color: #fff;
}
.projectTile--link:hover {
	.projectTile--overlay {
		opacity: 1;
		transform: scale(1.05);
	}
}
.projectTile--desc {
	font-size: 18px;
	text-align: center;
	margin-top: 10px;
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
.icon {
	width: 16px;
}
.githubIcon {
	margin-right: 7px;
	width: 20px;
}
.followIcon {
	margin-left: 5px;
	filter: invert(100%) sepia(0%) saturate(7495%) hue-rotate(296deg) brightness(93%) contrast(106%);
}

.githubDisabled {
	text-decoration: line-through;
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
	.projectTile--githubLink {
		color: #272727;
	}
	.projectTile--githubLink:hover {
		color: #f8b526;
	}
	.projectTile--githubLink:hover::before,
	.projectTile--githubLink:hover::after {
		color: #f8b526;
	}
	.projectTile--desc {
		color: #272727;
	}
	.projectTile::before {
		background: #f8b526;
		box-shadow: 0px 0px 3px 1px #f8b526;
	}

	.projectTile--overlay {
		background: rgba(248, 181, 38, 0);
	}
	.projectTile--link:hover {
		.projectTile--overlay {
			background: rgba(248, 181, 38, 0.8);
		}
	}
}
.dark {
	.githubIcon {
		filter: invert(100%) sepia(72%) saturate(48%) hue-rotate(230deg) brightness(116%) contrast(100%);
	}
	.projectTile--githubLink {
		color: #fff;
	}
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
	.projectTile--overlay {
		background: rgba(148, 75, 190, 0);
	}
	.projectTile--link:hover {
		.projectTile--overlay {
			background: rgba(148, 75, 190, 0.8);
		}
	}
}

@media (min-width: 841px) {
	.projectTile {
		width: 48%;
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
		padding: 20px;
	}
}
</style>
