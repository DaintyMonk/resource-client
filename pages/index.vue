<script lang="ts">
	import Vue from "vue";
	import VSectionWelcome from "~/components/v-section-welcome.vue";
	import VSectionFavorite from "~/components/v-section-favorite.vue";
	import VSectionAbout from "~/components/v-section-about.vue";
	import VSectionMobile from "~/components/v-section-mobile.vue";

	export default Vue.extend({
		name: "Home",
		components: {
			VSectionMobile,
			VSectionAbout,
			VSectionFavorite,
			VSectionWelcome,
		},
	});
</script>

<template>
	<div>
		<VSectionWelcome />
		<VSectionFavorite />
		<VSectionAbout />
		<VSectionMobile />
	</div>
</template>
