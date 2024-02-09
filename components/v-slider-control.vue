<script>
	export default {
		name: "VSliderControl",
		props: {
			controlIndex: {
				type: Number,
				default: () => 0,
			},
			currentSlide: {
				type: Number,
				default: () => 0,
			},
		},
		computed: {
			active() {
				return this.controlIndex - 1 === this.currentSlide;
			},
		},
	};
</script>

<template>
	<button v-if="active" class="slider__control-btn active" />
	<button v-else class="slider__control-btn" />
</template>

<style lang="scss" scoped>
	.slider__control-btn {
		width: 2.5rem;
		height: 0.25rem;
		margin-inline: 0.375rem;
		border: transparent;
		border-radius: 6.25rem;
		background-color: var(--clr-300);
		cursor: pointer;

		&:where(.active) {
			background-color: var(--clr-600);
		}
	}
</style>
