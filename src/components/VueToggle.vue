<template>
	<label v-bind:for="id" tabindex="0" v-on:keyup.enter="onChange">
		<div class="v-toggle" v-bind:class="isDisabled" v-bind:style="toggleStyle.containerStyle">
			<div class="v-toggle-circle" v-bind:style="toggleStyle.circleStyle">
				<span class="text" v-if="showText" v-bind:style="toggleStyle.textStyle">{{toggleStyle.text}}</span>
			</div>
		</div>
		<input v-bind:ref="id" type="checkbox" v-bind:id="id" v-bind:checked="value"
			v-on:change="onChange" v-bind:disabled="isDisabled.disabled" hidden />
	</label>
</template>

<script>

const DEFAULT_ACTIVE_COLOR = '#30d126';
const DEFAULT_INACTIVE_COLOR = '#ff3333';

function onChange(event) {
	if (event.type === 'keyup') {
		this.$refs[this.id].checked = !this.$refs[this.id].checked;
	}
	this.$emit('input', event.type === 'keyup' ? this.$refs[this.id].checked : event.target.checked);
}

function isDisabled() {
	return { disabled: this.$attrs.disabled };
}

function toggleStyle() {
	const widthParent = this.width;
	const heightParent = this.height;
	const widthCircle = this.height - 6;
	const heightCircle = this.height - 6;
	const translateX = this.value ? 3 : ((widthParent - widthCircle) - 3);
	const colorProperty = this.colorGradient ? 'background-image' : 'background-color';
	const containerStyle = {
		[colorProperty]: this.value ? this.activeColor : this.inactiveColor,
		height: `${heightParent}px`,
		width: `${widthParent}px`,
	};
	const circleStyle = {
		height: `${heightCircle}px`,
		transform: `translateX(${translateX}px)`,
		width: `${widthCircle}px`,
	};
	const textStyle = {
		color: this.value ? this.activeColor : this.inactiveColor,
	};
	const text = this.value ? this.activeText : this.inactiveText;
	return { containerStyle, circleStyle, textStyle, text };
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
		activeColor: {
			type: String,
			default: DEFAULT_ACTIVE_COLOR,
		},
		activeText: {
			type: String,
			default: 'On',
		},
		colorGradient: {
			type: Boolean,
			default: false,
		},
		height: {
			type: Number,
			default: 38.4,
		},
		inactiveColor: {
			type: String,
			default: DEFAULT_INACTIVE_COLOR,
		},
		inactiveText: {
			type: String,
			default: 'Off',
		},
		id: {
			type: [String, Number],
			required: true,
		},
		showText: {
			type: Boolean,
			default: false,
		},
		value: {
			type: Boolean,
			default: false,
		},
		width: {
			type: Number,
			default: 107.5,
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
	display: inline-block;
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
		box-shadow: 0 1px 2px 0 rgba(0, 0, 0, 0.5);
		position: absolute;
		margin-top: 3px;
		transition: transform 0.2s cubic-bezier(0,0,.2,1);
	}

	.text {
		font-weight: 900;
		left: 3%;
		padding: 20%;
		position: relative;
		top: 22%;
	}

}
</style>