<script>
	export default {
		name: "VBtnBurger",
		props: {
			open: {
				type: Boolean,
				default: () => false,
			},
		},
	};
</script>

<template>
	<div class="burger">
		<div class="burger__bar" :class="{ burger__bar_active: open }"></div>
		<div class="burger__bar" :class="{ burger__bar_active: open }"></div>
	</div>
</template>

<style lang="scss" scoped>
	.burger {
		flex-direction: column;
		justify-content: center;
		align-items: center;
		width: 2.75rem;
		height: 2.75rem;
		border: 0.0625rem solid var(--clr-700);
		border-radius: 6.25rem;
		cursor: pointer;

		&__bar {
			width: 1rem;
			height: 0;
			margin: 0.25rem;
			border: 0.09375rem solid var(--clr-700);
			transition: all 0.3s ease-in-out;

			&:first-child:where(&_active) {
				transform: rotate(-45deg) translateX(-3.5px) translateY(3.5px);
			}

			&:last-child:where(&_active) {
				transform: rotate(45deg) translateX(-3.5px) translateY(-3.5px);
			}
		}
	}
</style>
