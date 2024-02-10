<script lang="ts">
	import Vue from "vue";
	import VWelcome from "~/components/v-welcome.vue";
	import VFavorite from "~/components/v-favorite.vue";
	import VAbout from "~/components/v-about.vue";

	export default Vue.extend({
		name: "Home",
		components: { VAbout, VFavorite, VWelcome },
	});
</script>

<template>
	<div>
		<VWelcome />
		<VFavorite />
		<VAbout />
	</div>
</template>
