<script lang="ts">
	import Vue from "vue";
	import VAppStoreIcon from "~/components/icons/v-app-store-icon.vue";
	import VGooglePlayIcon from "~/components/icons/v-google-play-icon.vue";
	import VBtnStore from "~/components/v-btn-store.vue";

	export default Vue.extend({
		name: "VMobileSection",
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
			<VBtnStore
				class="mobile__btn"
				text="Available on the"
				store-name="App Store"
			>
				<VAppStoreIcon />
			</VBtnStore>
			<VBtnStore
				class="mobile__btn"
				text="Available on"
				store-name="Google Play"
			>
				<VGooglePlayIcon />
			</VBtnStore>
		</div>
		<img
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
			margin-right: 1rem;
		}
	}
</style>
