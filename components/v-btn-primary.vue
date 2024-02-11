<script lang="ts">
	import VIcon from "~/components/v-icon.vue";
	import VCoffeeCupIcon from "~/components/icons/v-coffee-cup-icon.vue";
	export default {
		name: "VBtnPrimary",
		components: { VCoffeeCupIcon, VIcon },
		props: {
			path: {
				type: String,
				default: () => null,
			},
			hash: {
				type: String,
				default: () => null,
			},
		},
	};
</script>

<template>
	<NuxtLink class="btn__link" :to="{ path: path, hash: hash }">
		<button class="btn_primary">
			<slot />
			<VIcon width="20" height="20" icon-color="none" stroke-color="none">
				<VCoffeeCupIcon />
			</VIcon>
		</button>
	</NuxtLink>
</template>

<style lang="scss" scoped>
	.btn {
		&__link {
			text-decoration: none;
		}

		&_primary {
			display: flex;
			align-items: center;
			justify-content: center;
			width: 12.5rem;
			height: 4rem;
			background-color: var(--clr-200);
			border-radius: 2.5rem;
			border-color: transparent;
			cursor: pointer;

			font-size: var(--fs-300);
			font-weight: var(--fw-bold);
			line-height: 1.5;
			color: var(--clr-700);

			& > svg {
				width: 0;
				opacity: 0;
				margin-left: 0.5rem;
				fill: transparent;
				stroke: var(--clr-700);
				transition: width 0.4s ease-in-out;
			}

			&:hover > svg {
				width: 20px;
				opacity: 1;
			}
		}
	}
</style>
