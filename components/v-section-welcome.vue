<script lang="ts">
	import VBtnPrimary from "~/components/v-btn-primary.vue";
	export default {
		name: "VSectionWelcome",
		components: { VBtnPrimary },
	};
</script>

<template>
	<section class="welcome">
		<video
			class="welcome__video"
			src="/welcome/video.mp4"
			poster="/welcome/video-poster.jpeg"
			autoplay
			loop
			muted
		></video>
		<div class="welcome__container">
			<h1 class="welcome__heading heading-text heading-text_big">
				<span class="text-accent">Enjoy</span> premium coffee at our charming
				cafe
			</h1>
			<p class="welcome__text">
				With its inviting atmosphere and delicious coffee options, the Coffee
				House Resource is a popular destination for coffee lovers and those
				seeking a warm and inviting space to enjoy their favorite beverage.
			</p>
			<VBtnPrimary path="/menu">Menu</VBtnPrimary>
		</div>
	</section>
</template>

<style lang="scss" scoped>
	.welcome {
		position: relative;
		height: 40.25rem;
		margin-bottom: 6.25rem;

		&__video {
			position: absolute;
			z-index: -1;
			width: 100%;
			height: 100%;
			object-fit: cover;
			border-radius: 2.5rem;
		}

		&__container {
			width: min(100%, 33.125rem + (6.25rem * 2));
			padding: 6.25rem;
		}

		&__heading {
			margin: 0 0 2.5rem 0;
			color: var(--clr-200);
		}

		&__text {
			margin-bottom: 2.5rem;
			color: var(--clr-200);
		}
	}

	@media (768px <= width < 1440px) {
		.welcome {
			&__container {
				width: min(100%, 33.125rem + (3.75rem * 2));
				padding: 6.25rem 3.75rem;
			}
		}
	}

	@media (width < 768px) {
		.welcome {
			height: 34.5rem;

			&__container {
				width: min(100%, 19.75rem + (1rem * 2));
				padding: 3.75rem 1rem;
			}
		}
	}
</style>
