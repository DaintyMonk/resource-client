<script>
	import VIcon from "./v-icon";
	export default {
		name: "VBtnStore",
		components: { VIcon },
		props: {
			text: {
				type: String,
				default: () => "Available on",
			},
			storeName: {
				type: String,
				default: () => "",
			},
		},
	};
</script>

<template>
	<div class="btn-store">
		<VIcon
			class="btn-store__icon"
			width="36"
			height="36"
			icon-color="none"
			stroke-color="none"
		>
			<slot />
		</VIcon>
		<div class="btn-store__content">
			<p class="btn-store__text main-text_caption">{{ text }}</p>
			<span class="btn-store__name btn-text">{{ storeName }}</span>
		</div>
	</div>
</template>

<style lang="scss" scoped>
	.btn-store {
		display: inline-flex;
		align-items: center;
		width: 12.5rem;
		height: 4rem;
		padding: 0.75rem 1.25rem;
		border: 0.06rem solid var(--clr-600);
		border-radius: 6.25rem;
		cursor: pointer;

		&__icon {
			fill: var(--clr-700);
		}

		&__content {
			margin-left: 0.5rem;
		}

		&__text {
			margin: 0 0 0.125rem 0;
			color: var(--clr-700);
		}

		&__name {
			color: var(--clr-700);
		}

		&:hover {
			background-color: var(--clr-600);
		}

		&:hover > &__icon {
			fill: var(--clr-200);
		}

		&:hover > &__content > &__text {
			color: var(--clr-200);
		}

		&:hover > &__content > &__name {
			color: var(--clr-200);
		}
	}
</style>
