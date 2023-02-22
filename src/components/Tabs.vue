<script setup>
import Tab from './Tab.vue';
import TabItem from './TabItem.vue';
import HobbyTile from './HobbyTile.vue';
import ArrowRightTop from './icons/ArrowRightTop.vue';
</script>
<template>
	<ul class="tabs">
		<li
			class="tab"
			:class="currentTab === tab.text_key ? `active` : ``"
			v-for="tab in tabs"
			:key="tab.text_key"
			@click="currentTab = tab.text_key"
		>
			<b>{{ $t(tab.text_key) }}</b>
		</li>
	</ul>
	<Tab class="tab--content" v-if="currentTab === 'about.university'">
		<TabItem class="tabItem--borders tabItem---extendedMargin"
			><h3 class="tab--contentHeader">{{ $t('university') }}</h3>
			<p>{{ $t('re-bechelor-dates') }}</p>
			<p>
				<b>{{ $t('bechelor') }}</b>
			</p>
			<p>{{ $t('field') }} {{ $t('res') }}</p>
		</TabItem>
		<TabItem class="tabItem--borders tabItem---extendedMargin"
			><h3 class="tab--contentHeader">{{ $t('university') }}</h3>
			<p>{{ $t('it-master-dates') }}</p>
			<p>
				<b>{{ $t('master') }}</b>
			</p>
			<p>{{ $t('field') }} {{ $t('it') }}</p>
			<p>{{ $t('spec') }}</p>
		</TabItem>
		<TabItem class="tabItem--borders tabItem---extendedMargin"
			><h3 class="tab--contentHeader">{{ $t('university') }}</h3>
			<p>{{ $t('it-bechelor-dates') }}</p>
			<p>
				<b>{{ $t('bechelor') }}</b>
			</p>
			<p>{{ $t('field') }} {{ $t('it') }}</p>
		</TabItem>
	</Tab>
	<Tab class="tab--content" v-if="currentTab === 'about.experience'"
		><TabItem class="tab--experience tabItem---layout">
			<img class="tab--contentImage" src="../assets/images/Lively.webp" alt="Logo" />
			<div class="tab--desc">
				<h2 class="tab--experienceHeader" v-html="$t('lively-desc')"></h2>
				<p class="tab--experienceDates">{{ $t('lively-dates') }}</p>
				<ul class="tab--experienceList">
					<li class="tab--experienceListItem" v-for="item in livelyExperience" :key="item.text_key">
						<ArrowRightTop class="icon tab--experienceIcon" /> {{ $t(item.text_key) }}
					</li>
				</ul>
			</div>
		</TabItem>
		<TabItem class="tab--experience tabItem---layout">
			<img class="tab--contentImage" src="../assets/images/TuOglosLogo.webp" alt="Logo" />
			<div class="tab--desc">
				<h2 class="tab--experienceHeader" v-html="$t('tuoglos-desc')"></h2>
				<p class="tab--experienceDates">{{ $t('tuoglos-dates') }}</p>
				<ul class="tab--experienceList">
					<li class="tab--experienceListItem" v-for="item in tuOglos" :key="item.text_key">
						<ArrowRightTop class="icon tab--experienceIcon" /> {{ $t(item.text_key) }}
					</li>
				</ul>
			</div>
		</TabItem></Tab
	>
	<Tab class="tab--content tabItem---layout" v-if="currentTab === 'about.hobbies'">
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
	</Tab>
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
		Tab,
		TabItem,
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
}
.tab {
	flex-shrink: 1;
	list-style: none;
	width: 30%;
	padding: 15px;
	border-radius: 10px;
	background: #fff;
	text-align: center;
	cursor: pointer;
}
.tab::before {
	content: '';
	position: absolute;
	bottom: 10px;
	left: 50%;
	transform: translateX(-50%);
	width: 0%;
	height: 1px;
}

.tab.active::before {
	width: 50%;
	transition: 0.5s ease-in-out;
}
.tab--content {
	margin: auto;
	width: 100%;
}

.tabItem---extendedMargin {
	margin: 50px 0px;
}
.tab--experience {
	padding: 20px 0px;
}
.tab--experienceHeader {
	text-align: center;
}
.tab--experienceDates {
	margin-top: 10px;
	text-align: center;
	font-weight: 700;
	padding-bottom: 5px;
}
.tab--experienceList {
	list-style: none;
	margin-top: 20px;
}
.tab--experienceListItem {
	font-size: 16px;
	line-height: 1.1;
	margin: 10px 0px;
}

.tab--desc {
	padding: 0px 10px;
}
.tabItem---layout {
	display: flex;
	flex-wrap: wrap;
	align-items: center;
	justify-content: space-around;
	gap: 30px;
}
.tab--contentHeader {
	text-decoration: underline;
}
.tab--contentImage {
	max-width: 60%;
}
.hobbyTile--image {
	width: 100%;
	object-fit: cover;
	border-radius: 20px;
}
.light {
	.tab,
	.tabItem {
		border: 1px solid #1f1f1f;
		transition: 0.1s ease-in-out;
	}
	.tab:hover {
		letter-spacing: 3px;
	}
	.active::before {
		background: #f8b526;
		box-shadow: 0px 0px 1px 1px #f8b526;
	}
	.tab--experienceDates {
		border-bottom: 1px solid #f8b526;
	}
	.tab--experienceIcon {
		filter: invert(72%) sepia(100%) saturate(831%) hue-rotate(339deg) brightness(101%) contrast(94%);
	}
}
.dark {
	.active::before {
		background: #944bbe;
		box-shadow: 0px 0px 1px 1px #944bbe;
	}
	.tab--experienceDates {
		border-bottom: 1px solid #944bbe;
	}
	.tab--experienceIcon {
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
		max-height: 200px;
		border-radius: 50px;
	}
	.tab--contentImage {
		max-width: 30%;
	}
	.tab--desc {
		width: 50%;
	}
}
@media (max-width: 600px) {
	.tabItem---layout {
		flex-direction: column;
	}
	.tabs {
		flex-direction: column;
	}
	.tab {
		margin-bottom: 15px;
		width: 100%;
	}
}
</style>
