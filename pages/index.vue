<script lang="ts">
	import Vue from "vue";
	import VWelcomeSection from "~/components/v-welcome-section.vue";
	import VFavoriteSection from "~/components/v-favorite-section.vue";
	import VAboutSection from "~/components/v-about-section.vue";

	export default Vue.extend({
		name: "Home",
		components: { VAboutSection, VFavoriteSection, VWelcomeSection },
	});
</script>

<template>
	<div>
		<VWelcomeSection />
		<VFavoriteSection />
		<VAboutSection />
	</div>
</template>
