<template>
	<div class="v-toggle-container">
		<label for="vue-toggle">
			<div class="v-toggle" v-bind:class="toggleStyle">
				<div class="v-toggle-circle" v-bind:class="toggleStyle">
				</div>
			</div>
			<input type="checkbox" id="vue-toggle"
				v-on:change="onChange" hidden />
		</label>
	</div>
</template>

<script>

function onChange(event) {
	this.$emit('input', event.target.checked);
}

function toggleStyle() {
	return this.value ? 'active' : 'inactive';
}

export default {
	name: 'v-toggle',
	computed: {
		toggleStyle,
	},
	methods: {
		onChange,
	},
	props: {
		value: {
			type: Boolean,
			default: false,
		},
	},
};
</script>

<style lang="scss" scoped>
.v-toggle-container {
	display: inline-block;
}
.v-toggle {
  border: solid 0.5px #d9d9d9;
  border-radius: 100px;
	cursor: pointer;
  height: 38.4px;
	position: relative;
	transition: background-color 0.2s ease-in-out;
  width: 107.5px;

	&.active {
		background-color: #30d126;
	}

	&.inactive {
		background-color: #ff3333;
	}

	.v-toggle-circle {
  	background-color: #fff;
		border-radius: 50%;
		bottom: 7%;
  	box-shadow: 0 1px 2px 0 rgba(0, 0, 0, 0.5);
  	height: 33.6px;
		position: absolute;
  	width: 33.6px;

		&.active {
			left: 0px;
			transform: translateX(0);
			transition: transform 0.2s cubic-bezier(0,0,.2,1);
		}

		&.inactive {
			transform: translateX(calc(107.5px - 33.5px));
			transition: transform 0.2s cubic-bezier(0,0,.2,1);
		}

	}

}
</style>