<template>
	<label v-bind:for="id">
		<div class="v-toggle" v-bind:class="isDisabled" v-bind:style="toggleStyle.containerStyle">
			<div class="v-toggle-circle" v-bind:style="toggleStyle.circleStyle">
			</div>
		</div>
		<input type="checkbox" v-bind:id="id"
			v-on:change="onChange" v-bind:disabled="isDisabled.disabled" hidden />
	</label>
</template>

<script>

function onChange(event) {
	this.$emit('input', event.target.checked);
}

function isDisabled() {
	return { disabled: this.$attrs.disabled };
}

function toggleStyle() {
	const widthParent = 107.5;
	const widthCircle = 33.5;
	const translateX = this.value ? 0 : (widthParent - widthCircle);

	const containerStyle = {
		'background-color': this.value ? '#30d126' : '#ff3333',
	};
	const circleStyle = {
		transform: `translateX(${translateX}px)`,
	};
	return { containerStyle, circleStyle };
}

export default {
	name: 'v-toggle',
	computed: {
		isDisabled,
		toggleStyle,
	},
	methods: {
		onChange,
	},
	props: {
		id: {
			type: [String, Number],
			required: true,
		},
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

	&.disabled {
		cursor: not-allowed;
		opacity: 0.4;
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
		transition: transform 0.2s cubic-bezier(0,0,.2,1);
  	width: 33.6px;
	}

}
</style>