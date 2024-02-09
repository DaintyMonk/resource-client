<script lang="ts">
	import Vue from "vue";
	import VWelcome from "~/components/v-welcome.vue";

	export default Vue.extend({
		name: "Home",
		components: { VWelcome },
	});
</script>

<template>
	<VWelcome />
</template>
