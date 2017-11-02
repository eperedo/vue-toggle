<template>
	<div id="app">
		<header>
			<span>Vue.js PWA</span>
		</header>
		<main>
			<v-toggle v-model="toggleValue" v-on:input="getValue" />
		</main>
	</div>
</template>

<script>
import VToggle from './components/VueToggle';

function getValue(value) {
	this.toggleValue = value;
}

export default {
	name: 'app',
	data() {
		return {
			toggleValue: false,
		};
	},
	components: {
		VToggle,
	},
	methods: {
		getValue,
	},
};
</script>

<style lang="scss">
html {
	font-size: 16px;
}
</style>
