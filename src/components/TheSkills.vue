<script setup>
import SkillBar from './SkillBar.vue';
import VueIcon from './icons/VueIcon.vue';
import PhpIcon from './icons/PhpIcon.vue';
import ReactIcon from './icons/ReactIcon.vue';
import CssIcon from './icons/CssIcon.vue';
import TsIcon from './icons/TsIcon.vue';
import JsIcon from './icons/JsIcon.vue';
</script>
<template>
	<div class="skills">
		<SkillBar name="Vue.js" width="40">
			<VueIcon class="skillbar--icon skillbar--icon---vue" />
		</SkillBar>
		<SkillBar name="React.js" width="30">
			<ReactIcon class="skillbar--icon skillbar--icon---react" />
		</SkillBar>
		<SkillBar name="Vanilla JS" width="60">
			<JsIcon class="skillbar--icon skillbar--icon---js" />
		</SkillBar>
		<SkillBar name="PHP" width="30">
			<PhpIcon class="skillbar--icon skillbar--icon---php" />
		</SkillBar>
		<SkillBar name="Typescript" width="35">
			<TsIcon class="skillbar--icon skillbar--icon---ts" />
		</SkillBar>
		<SkillBar name="CSS/SCSS" width="80">
			<CssIcon class="skillbar--icon skillbar--icon---css" />
		</SkillBar>
	</div>
</template>

<script>
export default {
	components: {
		SkillBar,
		VueIcon,
		JsIcon,
		TsIcon,
		CssIcon,
		ReactIcon,
		PhpIcon,
	},
};
</script>

<style lang="scss" scoped>
.skills {
	padding: 20px;
	border-radius: 10px;
	width: 100%;
	text-align: center;
}
.skillbar--icon {
	width: 50px;
}
.skillbar--icon---vue {
	filter: invert(55%) sepia(64%) saturate(344%) hue-rotate(99deg) brightness(97%) contrast(89%);
}
.skillbar--icon---css {
	filter: invert(23%) sepia(78%) saturate(2805%) hue-rotate(208deg) brightness(94%) contrast(105%);
}
.skillbar--icon---ts {
	filter: invert(32%) sepia(77%) saturate(1452%) hue-rotate(188deg) brightness(97%) contrast(88%);
}
.skillbar--icon---react {
	filter: invert(74%) sepia(39%) saturate(626%) hue-rotate(155deg) brightness(98%) contrast(90%);
}
.skillbar--icon---php {
	filter: invert(52%) sepia(8%) saturate(2154%) hue-rotate(198deg) brightness(88%) contrast(83%);
}
.skillbar--icon---js {
	filter: invert(97%) sepia(54%) saturate(5270%) hue-rotate(341deg) brightness(96%) contrast(92%);
}

.light {
	.skills {
		background: #fff;
	}
}
.dark {
	.skills {
		background: #272727;
	}
}
</style>
