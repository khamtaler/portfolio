<script setup>
import BaseTab from './BaseTab.vue';
import BaseTabContent from './BaseTabContent.vue';
import HobbyTile from './HobbyTile.vue';
import ArrowRightTop from './icons/ArrowRightTop.vue';
</script>
<template>
	<ul class="tabs">
		<li
			class="tabs--tab"
			:class="currentTab === tab.text_key ? `active` : ``"
			v-for="tab in tabs"
			:key="tab.text_key"
			@click="currentTab = tab.text_key"
		>
			<b class="tabs--name">{{ $t(tab.text_key) }}</b>
		</li>
	</ul>
	<BaseTab v-if="currentTab === 'about.university'">
		<BaseTabContent class="tab--university"
			><h3 class="tab--university-header">{{ $t('university') }}</h3>
			<p>{{ $t('re-bechelor-dates') }}</p>
			<p>
				<b>{{ $t('bechelor') }}</b>
			</p>
			<p>{{ $t('field') }} {{ $t('res') }}</p>
		</BaseTabContent>
		<BaseTabContent class="tab--university"
			><h3 class="tab--university-header">{{ $t('university') }}</h3>
			<p>{{ $t('it-master-dates') }}</p>
			<p>
				<b>{{ $t('master') }}</b>
			</p>
			<p>{{ $t('field') }} {{ $t('it') }}</p>
			<p>{{ $t('spec') }}</p>
		</BaseTabContent>
		<BaseTabContent class="tab--university"
			><h3 class="tab--university-header">{{ $t('university') }}</h3>
			<p>{{ $t('it-bechelor-dates') }}</p>
			<p>
				<b>{{ $t('bechelor') }}</b>
			</p>
			<p>{{ $t('field') }} {{ $t('it') }}</p>
		</BaseTabContent>
	</BaseTab>
	<BaseTab v-if="currentTab === 'about.experience'"
		><BaseTabContent class="tab--experience tab--experience---padding">
			<img class="tab--experience-logo" src="../assets/images/Lively.webp" alt="Logo" />
			<div class="tab--experience-desc">
				<h2 class="tab--experience-header" v-html="$t('lively-desc')"></h2>
				<p class="tab--experience-dates">{{ $t('lively-dates') }}</p>
				<ul class="tab--experience-list">
					<li
						class="tab--experience-listItem"
						v-for="item in livelyExperience"
						:key="item.text_key"
					>
						<ArrowRightTop class="icon tab--experience-icon" /> {{ $t(item.text_key) }}
					</li>
				</ul>
			</div>
		</BaseTabContent>
		<BaseTabContent class="tab--experience tab--experience---padding">
			<img class="tab--experience-logo" src="../assets/images/TuOglosLogo.webp" alt="Logo" />
			<div class="tab--experience-desc">
				<h2 class="tab--experience-header" v-html="$t('tuoglos-desc')"></h2>
				<p class="tab--experience-dates">{{ $t('tuoglos-dates') }}</p>
				<ul class="tab--experience-list">
					<li class="tab--experience-listItem" v-for="item in tuOglos" :key="item.text_key">
						<ArrowRightTop class="icon tab--experience-icon" /> {{ $t(item.text_key) }}
					</li>
				</ul>
			</div>
		</BaseTabContent></BaseTab
	>
	<BaseTab class="tab--hobbys" v-if="currentTab === 'about.hobbies'">
		<HobbyTile title="Snowboard">
			<img class="hobbyTile--image" src="../assets/images/Snowboard.webp" alt="Snowboard"
		/></HobbyTile>
		<HobbyTile :title="$t('travel')">
			<img class="hobbyTile--image" src="../assets/images/Travel.webp" alt="Travel"
		/></HobbyTile>
		<HobbyTile :title="$t('games')">
			<img class="hobbyTile--image" src="../assets/images/BoardGames.webp" alt="BoardGames"
		/></HobbyTile>
		<HobbyTile :title="$t('sightseeing')">
			<img class="hobbyTile--image" src="../assets/images/Sightseeing.webp" alt="Sightseeing"
		/></HobbyTile>
		<HobbyTile :title="$t('music')">
			<img class="hobbyTile--image" src="../assets/images/Music.webp" alt="Music"
		/></HobbyTile>
		<HobbyTile title="Sport">
			<img class="hobbyTile--image" src="../assets/images/Sport.webp" alt="Sport"
		/></HobbyTile>
	</BaseTab>
</template>

<script>
export default {
	data() {
		return {
			tabs: [
				{ text_key: 'about.university' },
				{ text_key: 'about.experience' },
				{ text_key: 'about.hobbies' },
			],
			livelyExperience: [
				{ text_key: 'livelyExperience.projects' },
				{ text_key: 'livelyExperience.forms' },
				{ text_key: 'livelyExperience.wordpress' },
				{ text_key: 'livelyExperience.mails' },
				{ text_key: 'livelyExperience.conservation' },
			],
			tuOglos: [{ text_key: 'tuOglos.vueLanding' }, { text_key: 'tuOglos.landing' }],
			currentTab: 'about.university',
		};
	},
	methods: {},
	components: {
		BaseTab,
		BaseTabContent,
		HobbyTile,
	},
};
</script>

<style lang="scss" scoped>
.tabs {
	display: flex;
	align-items: baseline;
	justify-content: space-between;
	width: 100%;
	margin-bottom: 30px;
	transition: 0ms;
}
.tabs--tab {
	flex-shrink: 1;
	list-style: none;
	width: 30%;
	padding: 15px;
	border-radius: 10px;
	text-align: center;
	cursor: pointer;
}

.tabs--tab:hover {
	letter-spacing: 3px;
	transition: 300ms ease-in-out;
}
.tabs--tab::before {
	content: '';
	position: absolute;
	bottom: 10px;
	left: 50%;
	transform: translateX(-50%);
	width: 0%;
	height: 1px;
}

.tabs--tab.active::before {
	width: 50%;
	transition: 0.5s ease-in-out;
}
.tab--university {
	margin: 50px 0px;
}
.tab--university::before,
.tab--university::after {
	content: '';
	position: absolute;
	width: 20px;
	height: 110%;
	background: transparent;
}
.tab--university::before {
	left: -5px;
	top: -5%;
}
.tab--university::after {
	right: -5px;
	top: -5%;
}

.tab--experience---padding {
	padding: 20px 0px;
}
.tab--experience-header {
	text-align: center;
}
.tab--experience-dates {
	margin-top: 10px;
	text-align: center;
	font-weight: 700;
	padding-bottom: 5px;
}
.tab--experience-list {
	list-style: none;
	margin-top: 20px;
}
.tab--experience-listItem {
	font-size: 16px;
	line-height: 1.1;
	margin: 10px 0px;
}

.tab--experience-desc {
	padding: 0px 10px;
	transition: 0ms;
}
.tab--hobbys,
.tab--experience {
	display: flex;
	flex-wrap: wrap;
	align-items: center;
	justify-content: space-around;
	gap: 30px;
}
.tab--university-header {
	text-decoration: underline;
}
.tab--experience-logo {
	max-width: 60%;
}
.hobbyTile--image {
	width: 100%;
	object-fit: cover;
	border-radius: 20px;
	height: 300px;
}
.light {
	.tabs--tab,
	.tab--content {
		border: 1px solid #272727;
	}
	.tabs--tab {
		background: #fff;
		color: #272727;
	}

	.active::before {
		background: #f8b526;
		box-shadow: 0px 0px 1px 1px #f8b526;
	}

	.tab--university::before {
		border-top: 10px solid #f8b526;
		border-bottom: 10px solid #f8b526;
		border-left: 10px solid #f8b526;
	}
	.tab--university::after {
		border-top: 10px solid #f8b526;
		border-right: 10px solid #f8b526;
		border-bottom: 10px solid #f8b526;
	}
	.tab--experience-dates {
		border-bottom: 1px solid #f8b526;
	}
	.tab--experience-icon {
		filter: invert(72%) sepia(100%) saturate(831%) hue-rotate(339deg) brightness(101%) contrast(94%);
	}
}

.dark {
	.tabs--tab {
		background: #272727;
		color: #fff;
	}
	.active::before {
		background: #944bbe;
		box-shadow: 0px 0px 1px 1px #944bbe;
	}
	.tab--university::before {
		border-top: 10px solid #944bbe;
		border-bottom: 10px solid #944bbe;
		border-left: 10px solid #944bbe;
	}
	.tab--university::after {
		border-top: 10px solid #944bbe;
		border-right: 10px solid #944bbe;
		border-bottom: 10px solid #944bbe;
	}
	.tab--experience-dates {
		border-bottom: 1px solid #944bbe;
	}
	.tab--experience-icon {
		filter: invert(39%) sepia(18%) saturate(2800%) hue-rotate(240deg) brightness(90%) contrast(92%);
	}
}
@media (max-width: 1200px) {
	.hobbyTile--image {
		aspect-ratio: 1;
	}
}
@media (min-width: 840px) {
	.tabs {
		width: 90%;
		margin: 0px auto 15px auto;
	}
	.hobbyTile--image {
		max-height: 300px;
		border-radius: 50px;
	}
	.tab--experience-logo {
		max-width: 30%;
	}
	.tab--experience-desc {
		width: 50%;
	}
}
@media (max-width: 600px) {
	.tab--hobbys,
	.tab--experience {
		flex-direction: column;
	}
	.tabs {
		flex-direction: column;
	}
	.tabs--tab {
		margin-bottom: 15px;
		width: 100%;
	}
}
</style>
