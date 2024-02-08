<script lang="ts">
	import PrimaryButton from "~/components/PrimaryButton.vue";
	export default {
		name: "WelcomeSection",
		components: { PrimaryButton },
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
			<PrimaryButton>Menu</PrimaryButton>
		</div>
	</section>
</template>

<style lang="scss" scoped>
	.welcome {
		position: relative;
		height: 40.25rem;

		&__video {
			position: absolute;
			z-index: -1;
			width: 100%;
			height: 100%;
			object-fit: cover;
			border-radius: 2.5rem;
		}

		&__container {
			width: 33.13rem;
			margin: 6.25rem 0 0 6.25rem;
		}

		&__heading {
			margin-bottom: 2.5rem;
			color: var(--clr-200);
		}

		&__text {
			margin-bottom: 2.5rem;
			color: var(--clr-200);
		}
	}
</style>
