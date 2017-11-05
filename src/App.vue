<template>
	<div id="app">
		<header>
			<h1 class="title">v-toggle</h1>
		</header>
		<main>
			<p>
				<pre>
					&#60;v-toggle id="v-t-default" v-model="toggleValue" /&#62;
				</pre>
				Default
				<v-toggle id="v-t-default" v-model="toggleValue" />
			</p>
			<div>
				<header>
					<h2 class="title">Custom Color
						<span>(any valid value for the background-color property)</span>
					</h2>
				</header>
			<p>
				<pre>
					&#60;v-toggle id="v-t-color" v-model="colorValue"
					active-color="rgba(0,0,0,.38)" inactive-color="peru" /&#62;
				</pre>
				Perú
				<v-toggle id="v-t-color" v-model="colorValue"
					active-color="rgba(0,0,0,.38)" inactive-color="peru" />
			</p>
			<p>
				<pre>
					&#60;v-toggle id="v-t-success" v-model="successValue"
						active-color="#4caf50" inactive-color="rgba(0,0,0,.38)"	/&#62;
				</pre>
				Success
				<v-toggle id="v-t-success" v-model="successValue"
					active-color="#4caf50" inactive-color="rgba(0,0,0,.38)" />
			</p>
			</div>
			<p>
				<pre>
					&#60;id="v-t-disabled" disabled="true" /&#62;
				</pre>
				Disabled:
				<v-toggle id="v-t-disabled" disabled="true" />
			</p>
			<div>
				<header>
					<h2 class="title">Custom Size</h2>
				</header>
				<p>
				<pre>
					&#60;v-toggle v-bind:width="36" v-bind:height="22"
						id="v-t-small" v-model="toggleSmall"	/&#62;
				</pre>
					Small
					<v-toggle v-bind:width="36" v-bind:height="22"
						id="v-t-small" v-model="toggleSmall" />
				</p>
			</div>
			<div>
				<header>
					<h2 class="title">Gradient Color</h2>
				</header>
				<p>
					<pre>
						&#60;v-toggle color-gradient
						active-color="linear-gradient(to left, #b3205f, #7d1642)"
						inactive-color="linear-gradient(to right, #20535e, #348899)"
						id="v-t-gradient" v-model="toggleGradient" /&#62;
					</pre>
					<v-toggle color-gradient
						active-color="linear-gradient(to left, #b3205f, #7d1642)"
						inactive-color="linear-gradient(to right, #20535e, #348899)"
						id="v-t-gradient" v-model="toggleGradient" />
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
			colorValue: false,
			successValue: false,
			toggleGradient: false,
			toggleSmall: false,
			toggleValue: true,
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

pre {
	background-color: #f8f8f8;
	padding: 1%;
	max-width: 500px;
	white-space: pre-line;
}

</style>
