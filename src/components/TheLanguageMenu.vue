<template>
	<div v-for="locale in $i18n.availableLocales" class="languageMenu">
		<label
			class="languageMenu--label"
			:for="locale"
			:class="{ active: lang === locale }"
			@click="toggleLanguage(locale)"
			>{{ locale }}</label
		>
		<input
			class="languageMenu--input"
			:id="locale"
			type="radio"
			v-model="$i18n.locale"
			:value="locale"
		/>
	</div>
</template>

<script>
export default {
	data() {
		return {
			lang: 'en',
		};
	},
	methods: {
		toggleLanguage(lang) {
			this.lang = lang;
		},
	},
};
</script>

<style lang="scss" scoped>
.languageMenu--label {
	color: #1f1f1f;
	text-transform: uppercase;
}
.languageMenu--label:hover {
	cursor: pointer;
}
.languageMenu--input {
	display: none;
}

.languageMenu--label.active::before {
	content: '';
	display: inline-block;
	position: absolute;
	background: #1f1f1f;
	width: 5px;
	height: 5px;
	border-radius: 50%;
}
.dark {
	.languageMenu--label {
		color: #fff;
	}
	.languageMenu--label.active::before {
		background: #fff;
	}
}

@media (min-width: 841px) {
	.languageMenu--label.active {
		left: 10px;
	}
	.languageMenu--label.active::before {
		left: -10px;
		top: 50%;
		transform: translateY(-50%);
	}
}
@media (max-width: 840px) {
	.languageMenu--label.active:before {
		top: -10px;
		left: 50%;
		transform: translateX(-50%);
	}
	.languageMenu--label.active {
		top: 10px;
	}
}
</style>
