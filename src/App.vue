<template>
	<div id="app">
		<header>
			<h1 class="title">v-toggle</h1>
		</header>
		<main>
			<p>
				Default
				<v-toggle id="v-t-default" v-model="toggleValue" v-on:input="getValue('toggleValue')" />
			</p>
			<div>
				<header>
					<h2 class="title">Custom Color
						<span>(any valid value for the background-color property)</span>
					</h2>
				</header>
			<p>
				Perú
				<v-toggle id="v-t-color" v-model="colorValue" v-on:input="getValue('colorValue')"
					active-color="rgba(0,0,0,.38)" inactive-color="peru" />
			</p>
			<p>
				Success
				<v-toggle id="v-t-success" v-model="successValue" v-on:input="getValue('successValue')"
					active-color="#4caf50" inactive-color="rgba(0,0,0,.38)" />
			</p>
			</div>
			<p>
				Disabled:
				<v-toggle id="v-t-disabled" disabled="true" />
			</p>
			<div>
				<header>
					<h2 class="title">Custom Size</h2>
				</header>
				<p>
					Small
					<v-toggle v-bind:width="36" v-bind:height="22"
						id="v-t-small" v-model="toggleSmall" v-on:input="getValue('toggleSmall')" />
				</p>
			</div>
		</main>
	</div>
</template>

<script>
import VToggle from './components/VueToggle';

function getValue(fieldName) {
	this[fieldName] = !this[fieldName];
}

export default {
	name: 'app',
	data() {
		return {
			successValue: true,
			colorValue: true,
			toggleValue: true,
			toggleSmall: true,
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
