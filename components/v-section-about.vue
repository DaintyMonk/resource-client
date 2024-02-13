<script>
	export default {
		name: "VSectionAbout",
		data() {
			return {
				aboutImgs: ["about-1", "about-2", "about-3", "about-4"],
			};
		},
	};
</script>

<template>
	<section id="about" class="about">
		<h2 class="about__heading heading-text heading-text_medium">
			Resource is
			<span class="text-accent">the perfect and cozy place</span> where you can
			enjoy a variety of hot beverages, relax, catch up with friends, or get
			some work done.
		</h2>
		<div class="about__container">
			<div v-for="(img, index) in aboutImgs" :key="index" class="about__img">
				<img :src="require(`~/assets/imgs/about/${img}.jpeg`)" :alt="img" />
			</div>
		</div>
	</section>
</template>

<style lang="scss" scoped>
	.about {
		margin-bottom: 6.25rem;

		&__heading {
			margin: 0 0 2.5rem 0;
			color: var(--clr-700);
		}

		&__container {
			display: flex;
			flex-flow: column wrap;
			gap: 2.5rem;
			height: 66.26rem;
			overflow: hidden;
		}

		&__img {
			position: relative;
			width: 41.25rem;
			height: 36.88rem;
			border: transparent;
			border-radius: 1.25rem;
			overflow: hidden;

			&:not(&:first-child, &:last-child) {
				height: 26.88rem;
			}

			& > img {
				position: absolute;
				top: -4.25rem;
				left: -2.06rem;
				right: -2.06rem;
				bottom: -4.25rem;
				width: 45.375rem;
				max-width: 45.375rem;
				height: 45.375rem;
				object-fit: cover;
				object-position: center;

				transition: transform 0.5s ease-in-out;

				&:hover {
					transform: scale(0.91);
				}
			}

			&:not(&:first-child, &:last-child) > img {
				top: -9.25rem;
				bottom: -9.25rem;
			}
		}
	}

	@media (768px <= width < 1440px) {
		.about {
			&__container {
				width: 43rem;
				height: 100%;
				margin-inline: auto;
			}

			&__img {
				width: 100%;

				&:not(&:first-child, &:last-child) {
					display: none;
				}

				& > img {
					position: absolute;
					top: -2.25rem;
					left: -2.1875rem;
					right: -2.1875rem;
					bottom: -2.25rem;
					width: 47.38rem;
					max-width: 47.38rem;
					height: 42.38rem;

					&:hover {
						transform: scale(0.91);
					}
				}
			}
		}
	}

	@media (width < 768px) {
		.about {
			&__container {
				width: 21.75rem;
				height: 100%;
				margin-inline: auto;
			}

			&__img {
				width: 100%;

				&:not(&:first-child, &:last-child) {
					display: none;
				}

				& > img {
					position: absolute;
					top: -4.25rem;
					left: -11.8125rem;
					right: -11.8125rem;
					bottom: -4.25rem;
					width: 45.375rem;
					max-width: 45.375rem;
					height: 45.375rem;

					&:hover {
						transform: scale(0.91);
					}
				}
			}
		}
	}
</style>
