<script>
	export default {
		name: "VIcon",
		props: {
			iconName: {
				type: String,
				default: "box",
			},
			width: {
				type: [Number, String],
				default: 18,
			},
			height: {
				type: [Number, String],
				default: 18,
			},
			iconColor: {
				type: String,
				default: "#000",
			},
			strokeColor: {
				type: String,
				default: "#000",
			},
		},
		computed: {
			viewBox() {
				return `0 0 ${this.width} ${this.height}`;
			},
			iconColorState() {
				return this.iconColor === "none" ? "" : this.iconColor;
			},
			strokeColorState() {
				return this.strokeColor === "none" ? "" : this.strokeColor;
			},
		},
	};
</script>

<template>
	<svg
		xmlns="http://www.w3.org/2000/svg"
		:width="width"
		:height="height"
		:viewBox="viewBox"
		:aria-labelledby="iconName"
	>
		<g :fill="iconColorState" :stroke="strokeColorState">
			<slot />
		</g>
	</svg>
</template>

<style scoped></style>
