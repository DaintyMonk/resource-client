<script>
	export default {
		name: "VBtnSecondary",
	};
</script>

<template>
	<button class="btn_secondary btn-text">
		<slot />
	</button>
</template>

<style lang="scss" scoped>
	.btn_secondary {
		height: 2.75rem;
		border: 0.0625rem solid var(--clr-700);
		border-radius: 6.25rem;
		background-color: transparent;
		color: var(--clr-700);
		cursor: pointer;

		&:hover {
			background-color: var(--clr-600);
			color: var(--clr-200);
		}
	}
</style>
