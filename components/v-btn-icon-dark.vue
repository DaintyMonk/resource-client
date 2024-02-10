<script>
	import VIcon from "./v-icon";
	export default {
		name: "VBtnIconDark",
		components: { VIcon },
	};
</script>

<template>
	<button class="btn-icon_dark">
		<VIcon width="24" height="24" stroke-color="none">
			<slot />
		</VIcon>
	</button>
</template>

<style lang="scss" scoped>
	.btn-icon_dark {
		width: 3.75rem;
		height: 3.75rem;
		display: flex;
		align-items: center;
		justify-content: center;
		background-color: transparent;
		border: 0.06rem solid var(--clr-600);
		border-radius: 6.25rem;
		cursor: pointer;

		&:hover {
			background-color: var(--clr-600);
		}

		& > svg {
			stroke: var(--clr-600);
		}

		&:hover > svg {
			stroke: var(--clr-200);
		}
	}
</style>
