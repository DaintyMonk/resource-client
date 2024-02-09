<script lang="js">
	import VCarouselItem from "~/components/v-carousel-item.vue";
	import VSliderControl from "~/components/v-slider-control";
	export default {
		name: "VCarousel",
		components: { VSliderControl, VCarouselItem },
		props: {
			carouselData: {
				type: Array,
				default: () => [],
			},
		},
		data() {
			return {
				currentSlideIndex: 0,
				touch: {
					startX: 0,
					endX:0
				}
			};
		},
		computed: {
			listPosition() {
				return {
					transform: "translateX(-" + this.currentSlideIndex * 100 + "%)",
				};
			},

		},
		methods: {
			prevSlide() {
				if (this.currentSlideIndex > 0) {
					this.currentSlideIndex--;
				}
			},
			nextSlide() {
				if (this.currentSlideIndex < this.carouselData.length - 1) {
					this.currentSlideIndex++;
				}
			},
			touchStart(event) {
				this.touch.startX = event.touches[0].clientX;
				this.touch.endX = 0;
			},
			touchMove(event) {
				this.touch.endX =event.touches[0].clientX;
			},
			touchEnd() {
				if(!this.touch.endX || Math.abs(this.touch.endX - this.touch.startX) < 20)
					return;

				if(this.touch.endX < this.touch.startX)
					this.nextSlide();
				else
					this.prevSlide();
			},
			selectSlide(id) {
				this.currentSlideIndex = id - 1;
			}
		},
	};
</script>

<template>
	<div>
		<div class="slider">
			<button class="slider__btn" @click="prevSlide">
				<svg
					class="slider__btn-icon"
					width="14"
					height="14"
					viewBox="0 0 14 14"
					fill="none"
					xmlns="http://www.w3.org/2000/svg"
				>
					<path
						d="M13.5 7H1M1 7L7 1M1 7L7 13"
						stroke-linecap="round"
						stroke-linejoin="round"
					/>
				</svg>
			</button>
			<ul class="slider__list" role="list">
				<li
					v-for="item in carouselData"
					:key="item.id"
					class="slider__item"
					:style="listPosition"
					@touchstart="touchStart($event)"
					@touchmove="touchMove($event)"
					@touchend="touchEnd"
				>
					<VCarouselItem :item-data="item" />
				</li>
			</ul>
			<button class="slider__btn" @click="nextSlide">
				<svg
					class="slider__btn-icon"
					width="14"
					height="14"
					viewBox="0 0 14 14"
					fill="none"
					xmlns="http://www.w3.org/2000/svg"
				>
					<path
						d="M1 7H13.5M13.5 7L7.5 1M13.5 7L7.5 13"
						stroke-linecap="round"
						stroke-linejoin="round"
					/>
				</svg>
			</button>
		</div>
		<div class="slider__control">
			<VSliderControl
				v-for="item in carouselData"
				:key="item.id"
				:control-index="item.id"
				:current-slide="currentSlideIndex"
				@click.native="selectSlide(item.id)"
			/>
		</div>
	</div>
</template>

<style lang="scss" scoped>
	.slider {
		display: flex;
		align-items: center;
		justify-content: space-between;
		margin-bottom: 2.5rem;

		&__btn {
			width: 3.75rem;
			height: 3.75rem;
			display: flex;
			align-items: center;
			justify-content: center;
			background-color: transparent;
			border: 0.06rem solid var(--clr-600);
			border-radius: 6.25rem;

			&:hover {
				background-color: var(--clr-600);
			}

			&-icon {
				stroke: var(--clr-600);
			}

			&:hover > &-icon {
				stroke: var(--clr-200);
			}

			&:first-child {
				margin-left: 0.25rem;
			}

			&:last-child {
				margin-right: 0.25rem;
			}
		}

		&__list {
			display: flex;
			max-width: 30rem;
			padding: 0;
			margin: 0;
			overflow: hidden;
		}

		&__item {
			transition: all 0.5s ease-in-out;
		}

		&__control {
			display: flex;
			justify-content: center;
		}
	}
</style>
