<script lang="ts">
	import VHeaderSection from "~/components/v-header-section.vue";
	import VFooterSection from "~/components/v-footer-section.vue";
	export default {
		components: { VFooterSection, VHeaderSection },
	};
</script>

<template>
	<div class="content-grid full-width">
		<VHeaderSection />
		<Nuxt />
		<VFooterSection />
	</div>
</template>

<style lang="scss" scoped>
	.content-grid,
	.full-width {
		--padding-inline: 2.5rem;
		--content-max-width: 85rem;

		display: grid;
		grid-template-columns:
			[full-width-start] minmax(var(--padding-inline), 1fr)
			[content-start] min(
				100% - (var(--padding-inline) * 2),
				var(--content-max-width)
			)
			[content-end]
			minmax(var(--padding-inline), 1fr) [full-width-end];

		> :not(.full-width),
		.full-width > :not(.full-width) {
			grid-column: content;
		}

		> .full-width {
			grid-column: full-width;
		}
	}
</style>
