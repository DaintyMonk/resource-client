<script lang="ts">
	import Vue, { PropOptions } from "vue";

	interface Card {
		id: number;
		img: string;
		name: string;
		description: string;
		price: string;
	}

	export default Vue.extend({
		name: "VCarouselItem",
		props: {
			itemData: {
				type: Object,
				default: () => {},
			} as PropOptions<Card>,
		},
	});
</script>

<template>
	<div class="card">
		<img
			class="card__img"
			:src="require(`~/assets/imgs/favorite/${itemData.img}.png`)"
			:alt="itemData.name"
			width="480"
			height="480"
		/>
		<h3 class="card__name heading-text heading-text_small">
			{{ itemData.name }}
		</h3>
		<p class="card__description main-text_medium">{{ itemData.description }}</p>
		<h3 class="card__price heading-text heading-text_small">
			{{ itemData.price }}
		</h3>
	</div>
</template>

<style lang="scss" scoped>
	.card {
		width: 30rem;

		&__img {
			width: 100%;
			height: 30rem;
			object-fit: cover;
		}

		&__name {
			margin: 1.25rem 0 1rem 0;
			text-align: center;
			color: var(--clr-700);
		}

		&__description {
			margin: 0 0 1rem 0;
			text-align: center;
			color: var(--clr-700);
		}

		&__price {
			margin: 0;
			text-align: center;
			color: var(--clr-700);
		}
	}

	@media (width < 768px) {
		.card {
			width: 21.75rem;

			&__img {
				height: 21.75rem;
			}
		}
	}
</style>
