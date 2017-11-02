<template>
	<div id="app">
		<header>
			<h1 class="title">v-toggle</h1>
		</header>
		<main>
			<p>
				Default
				<v-toggle id="v-t-default" v-model="toggleValue" v-on:input="getValue" />
			</p>
			<p>
				Disabled:
				<v-toggle id="v-t-disabled" disabled="true" />
			</p>
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
.title {
	text-align: center;
}
</style>
