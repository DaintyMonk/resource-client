<script lang="ts">
	import Vue from "vue";
	import VAppStoreIcon from "~/components/icons/v-app-store-icon.vue";
	import VGooglePlayIcon from "~/components/icons/v-google-play-icon.vue";
	import VBtnStore from "~/components/v-btn-store.vue";

	export default Vue.extend({
		name: "VSectionMobile",
		components: { VBtnStore, VGooglePlayIcon, VAppStoreIcon },
	});
</script>

<template>
	<section id="mobile" class="mobile">
		<div class="mobile__content">
			<h2 class="mobile__heading heading-text heading-text_medium">
				<span class="text-accent">Download</span> our apps to start ordering
			</h2>
			<p class="mobile__text main-text_medium">
				Download the Resource app today and experience the comfort of ordering
				your favorite coffee from wherever you are
			</p>
			<div class="mobile__btn-container">
				<VBtnStore text="Available on the" store-name="App Store">
					<VAppStoreIcon />
				</VBtnStore>
				<VBtnStore text="Available on" store-name="Google Play">
					<VGooglePlayIcon />
				</VBtnStore>
			</div>
		</div>
		<img
			class="mobile__img"
			src="/mobile/mobile-screens.png"
			alt="mobile-screens"
			width="630"
			height="630"
		/>
	</section>
</template>

<style lang="scss" scoped>
	.mobile {
		display: flex;
		align-items: center;
		justify-content: space-between;
		flex-wrap: wrap;
		margin-bottom: 6.25rem;

		&__content {
			max-width: 39.375rem;
		}

		&__heading {
			margin: 0 0 2.5rem 0;
			color: var(--clr-700);
		}

		&__text {
			margin: 0 0 2.5rem 0;
			color: var(--clr-700);
		}

		&__btn {
			&-container {
				display: flex;
				flex-flow: row wrap;
				justify-content: space-between;
				width: min(26.25rem, 100%);
			}
		}
	}

	@media (768px <= width < 1440px) {
		.mobile {
			&__content {
				max-width: 100%;
			}

			&__img {
				margin: 6.25rem auto 0;
			}
		}
	}

	@media (width < 768px) {
		.mobile {
			&__content {
				max-width: 100%;
			}

			&__btn {
				&-container {
					flex-flow: column nowrap;
					height: 9.25rem;
				}
			}

			&__img {
				height: 21.75rem;
				margin: 2.5rem auto 0;
			}
		}
	}
</style>
