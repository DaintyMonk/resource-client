<script>
	import VIcon from "./v-icon";
	export default {
		name: "VBtnIconLight",
		components: {
			VIcon,
		},
	};
</script>

<template>
	<button class="btn-icon_light">
		<VIcon width="24" height="24" icon-color="transparent" stroke-color="none">
			<slot />
		</VIcon>
	</button>
</template>

<style lang="scss" scoped>
	.btn-icon_light {
		width: 3.75rem;
		height: 3.75rem;
		display: flex;
		align-items: center;
		justify-content: center;
		background-color: transparent;
		border: 0.06rem solid var(--clr-300);
		border-radius: 6.25rem;

		&:hover {
			background-color: var(--clr-200);
		}

		& > svg {
			stroke: var(--clr-200);
		}

		&:hover > svg {
			stroke: var(--clr-700);
		}
	}
</style>
