<script setup>
import Tab from './Tab.vue';
import TabItem from './TabItem.vue';
import HobbyTile from './HobbyTile.vue';
</script>
<template>
	<ul class="tabs">
		<li
			class="tab"
			:class="currentTab === tab ? `active` : ``"
			v-for="(tab, index) in tabs"
			:key="index"
			@click="currentTab = tab"
		>
			<b>{{ tab }}</b>
		</li>
	</ul>
	<Tab class="tab--content" v-if="currentTab === 'University'">
		<TabItem
			><h3 class="tab--contentHeader">Cracow University of Technology</h3>
			<p>September 2022 - now</p>
			<p><b>Bechelor Degree</b></p>
			<p>Field of study: Renewable energy sources</p>
		</TabItem>
		<TabItem
			><h3 class="tab--contentHeader">Cracow University of Technology</h3>
			<p>February 2021 - September 2022</p>
			<p><b>Master Degree</b></p>
			<p>Field of study: IT</p>
			<p>Spec: Data Science</p>
		</TabItem>
		<TabItem
			><h3 class="tab--contentHeader">Cracow University of Technology</h3>
			<p>October 2017 - January 2021</p>
			<p><b>Bechelor Degree</b></p>
			<p>Field of study: IT</p>
		</TabItem>
	</Tab>
	<Tab class="tab--content" v-if="currentTab === 'Experience'"
		><TabItem class="tab--experience tabItem---layout">
			<img class="tab--contentImage" src="../assets/images/Lively.webp" alt="Logo" />
			<div class="tab--desc">
				<h3>
					Specjaliści od świata online. <br />
					Nieustająco podążają i uczą się nowinek technologicznych, aby klienci korzystali tylko z
					najlepszych narzędzi. Kreują wirtualną rzeczywistość, realizują każde wydarzenie.
				</h3>
			</div>
		</TabItem>
		<TabItem class="tab--experience tabItem---layout">
			<img class="tab--contentImage" src="../assets/images/TuOglosLogo.webp" alt="Logo" />
			<div class="tab--desc">
				<h3>Grupa 133 portali łącząca Polaków w Polsce i na całym świecie</h3>
			</div>
		</TabItem></Tab
	>
	<Tab class="tab--content tabItem---layout" v-if="currentTab === 'Hobbies'">
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
			tabs: ['University', 'Experience', 'Hobbies'],
			currentTab: 'University',
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
	width: 100%;
	text-align: center;
	cursor: pointer;
}
.active::before {
	content: '';
	position: absolute;
	bottom: -5px;
	left: 50%;
	transform: translateX(-50%);
	width: 50%;
	height: 1px;
}
.tab--content {
	margin: auto;
	width: 100%;
}
.tab--experience {
	padding: 20px 0px;
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
	.active::before {
		background: #000;
		box-shadow: 0px 0px 3px 1px #000;
	}
}
.dark {
	.active::before {
		background: #471564;
		box-shadow: 0px 0px 3px 1px #471564;
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
}
</style>
