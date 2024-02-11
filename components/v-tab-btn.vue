<script>
	export default {
		name: "VTabBtn",
		props: {
			tabName: {
				type: String,
				default: () => "",
			},
			currentTabIndex: {
				type: Number,
				default: () => 0,
			},
			currentMenuIndex: {
				type: Number,
				default: () => 0,
			},
		},
		computed: {
			active() {
				return this.currentTabIndex === this.currentMenuIndex;
			},
		},
	};
</script>

<template>
	<div v-if="active" class="tab-btn active">
		<div class="tab-btn__icon btn-text"><slot /></div>
		<span class="tab-btn__text btn-text">{{ tabName }}</span>
	</div>
	<div v-else class="tab-btn">
		<div class="tab-btn__icon btn-text"><slot /></div>
		<span class="tab-btn__text btn-text">{{ tabName }}</span>
	</div>
</template>

<style lang="scss" scoped>
	.tab-btn {
		display: flex;
		align-items: center;
		justify-content: space-between;
		border: 0.06rem solid var(--clr-300);
		border-radius: 6.25rem;
		cursor: pointer;

		&__icon {
			display: flex;
			align-items: center;
			justify-content: center;
			margin: 0.5rem;
			width: 1.88rem;
			height: 1.88rem;
			background-color: var(--clr-300);
			border-radius: 6.25rem;
			text-align: center;
			color: var(--clr-700);
		}

		&__text {
			margin-right: 1rem;
			color: var(--clr-700);
		}

		&:hover,
		&:where(.active) {
			background-color: var(--clr-600);
			border-color: var(--clr-600);
		}

		&:hover > &__icon,
		&:where(.active) > &__icon {
			background-color: var(--clr-200);
		}

		&:hover > &__text,
		&:where(.active) > &__text {
			color: var(--clr-200);
		}
	}
</style>
