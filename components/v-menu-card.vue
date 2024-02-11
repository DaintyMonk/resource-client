<script>
	export default {
		name: "VMenuCard",
		props: {
			itemType: {
				type: String,
				default: () => "",
			},
			img: {
				type: String,
				default: () => "",
			},
			name: {
				type: String,
				default: () => "",
			},
			description: {
				type: String,
				default: () => "",
			},
			price: {
				type: String,
				default: () => "",
			},
		},
	};
</script>

<template>
	<div class="menu-card">
		<div class="menu-card__img">
			<img :src="require(`~/assets/imgs/${itemType}/${img}.png`)" :alt="name" />
		</div>
		<div class="menu-card__content">
			<div class="menu-card__content-information">
				<h3 class="menu-card__name heading-text heading-text_small">
					{{ name }}
				</h3>
				<p class="menu-card__description main-text_medium">{{ description }}</p>
			</div>
			<h3 class="menu-card__price heading-text heading-text_small">
				{{ price }}
			</h3>
		</div>
	</div>
</template>

<style lang="scss" scoped>
	.menu-card {
		width: 19.375rem;
		border: 0.0625rem solid var(--clr-300);
		border-radius: 2.5rem;

		&__img {
			position: relative;
			width: 100%;
			height: 19.375rem;
			border: transparent;
			border-radius: 2.5rem;
			overflow: hidden;

			& > img {
				position: absolute;
				top: -0.9375rem;
				left: -0.9375rem;
				right: -0.9375rem;
				bottom: -0.9375rem;
				width: 21.25rem;
				max-width: 21.25rem;
				height: 21.25rem;
				object-fit: cover;
				object-position: center;

				transition: transform 0.5s ease-in-out;

				&:hover {
					transform: scale(0.91);
				}
			}
		}

		&__content {
			display: flex;
			flex-flow: column wrap;
			justify-content: space-between;
			height: 12.15rem;
			padding: 1.25rem;
		}

		&__name,
		&__description,
		&__price {
			margin: 0;
			color: var(--clr-700);
		}

		&__name {
			margin-bottom: 0.75rem;
		}
	}
</style>
