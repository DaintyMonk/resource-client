<script lang="js">
	import VCarouselItem from "~/components/v-carousel-item.vue";
	import VCarouselControl from "~/components/v-carousel-control";
	import VBtnIconDark from "~/components/v-btn-icon-dark";
	import VArrowLeftIcon from "~/components/icons/v-arrow-left-icon";
	import VArrowRightIcon from "~/components/icons/v-arrow-right-icon";
	export default {
		name: "VCarousel",
		components: { VArrowRightIcon, VArrowLeftIcon, VBtnIconDark, VCarouselControl, VCarouselItem },
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
			<VBtnIconDark class="slider__btn" @click.native="prevSlide">
				<VArrowLeftIcon />
			</VBtnIconDark>
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
			<VBtnIconDark class="slider__btn" @click.native="nextSlide">
				<VArrowRightIcon />
			</VBtnIconDark>
		</div>
		<div class="slider__control">
			<VCarouselControl
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

	@media (768px <= width < 1440px) {
		.slider {
			&__btn {
				&:first-child {
					margin-left: 0;
				}

				&:last-child {
					margin-right: 0;
				}
			}
		}
	}
</style>
