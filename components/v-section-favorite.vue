<script lang="ts">
	import VCarousel from "~/components/v-carousel.vue";
	export default {
		name: "VSectionFavorite",
		components: { VCarousel },
		data() {
			return {
				sliderItems: [
					{
						id: 1,
						img: "coffee-slider-1",
						name: "S’mores Frappuccino",
						description:
							"This new drink takes an espresso and mixes it with brown sugar and cinnamon before being topped with oat milk.",
						price: "$5.50",
					},
					{
						id: 2,
						img: "coffee-slider-2",
						name: "Caramel Macchiato",
						description:
							"Fragrant and unique classic espresso with rich caramel-peanut syrup, with cream under whipped thick foam.",
						price: "$5.00",
					},
					{
						id: 3,
						img: "coffee-slider-3",
						name: "Ice coffee",
						description:
							"A popular summer drink that tones and invigorates. Prepared from coffee, milk and ice.",
						price: "$4.50",
					},
				],
			};
		},
	};
</script>

<template>
	<section id="favorite" class="favorite">
		<h2 class="favorite__heading heading-text heading-text_medium">
			Choose your <span class="text-accent">favorite</span> coffee
		</h2>
		<VCarousel :carousel-data="sliderItems" />
	</section>
</template>

<style lang="scss" scoped>
	.favorite {
		margin-bottom: 6.25rem;

		&__heading {
			margin: 0 0 2.5rem 0;
			text-align: center;
			color: var(--clr-700);
		}
	}
</style>
