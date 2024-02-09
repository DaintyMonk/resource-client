<script lang="ts">
	export default {
		name: "VPrimaryBtn",
	};
</script>

<template>
	<NuxtLink class="btn__link" cl to="/">
		<button class="btn_primary">
			<slot />
			<img src="/icons/coffee-cup.svg" alt="coffee-cup" />
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

			& > img {
				width: 0;
				opacity: 0;
				margin-left: 0.5rem;
				transition: width 0.4s ease-in-out;
			}

			&:hover > img {
				width: 20px;
				opacity: 1;
			}
		}
	}
</style>
