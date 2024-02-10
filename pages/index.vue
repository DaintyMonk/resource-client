<script lang="ts">
	import Vue from "vue";
	import VWelcomeSection from "~/components/v-welcome-section.vue";
	import VFavoriteSection from "~/components/v-favorite-section.vue";
	import VAboutSection from "~/components/v-about-section.vue";
	import VMobileSection from "~/components/v-mobile-section.vue";

	export default Vue.extend({
		name: "Home",
		components: {
			VMobileSection,
			VAboutSection,
			VFavoriteSection,
			VWelcomeSection,
		},
	});
</script>

<template>
	<div>
		<VWelcomeSection />
		<VFavoriteSection />
		<VAboutSection />
		<VMobileSection />
	</div>
</template>
