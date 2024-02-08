<script lang="ts">
	import Vue from "vue";
	import WelcomeSection from "~/components/WelcomeSection.vue";

	export default Vue.extend({
		name: "Home",
		components: { WelcomeSection },
	});
</script>

<template>
	<WelcomeSection />
</template>
