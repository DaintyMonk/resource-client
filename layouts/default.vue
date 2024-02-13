<script lang="ts">
	import VSectionHeader from "~/components/v-section-header.vue";
	import VSectionFooter from "~/components/v-section-footer.vue";
	export default {
		components: { VSectionFooter, VSectionHeader },
	};
</script>

<template>
	<div class="content-grid full-width">
		<VSectionHeader />
		<Nuxt />
		<VSectionFooter />
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

	@media (width < 768px) {
		.content-grid,
		.full-width {
			--padding-inline: 1rem;
		}
	}
</style>
