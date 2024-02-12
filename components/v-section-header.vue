<script lang="ts">
	import VDesktopMenu from "~/components/v-desktop-menu.vue";
	export default {
		name: "VSectionHeader",
		components: { VDesktopMenu },
		data() {
			return {
				anchorLinks: [
					{
						path: "/",
						hash: "favorite",
						text: "Favorite Coffee",
					},
					{
						path: "/",
						hash: "about",
						text: "About",
					},
					{
						path: "/",
						hash: "mobile",
						text: "Mobile App",
					},
					{
						path: "/",
						hash: "contact",
						text: "Contact us",
					},
				],
			};
		},
	};
</script>

<template>
	<header class="header">
		<VDesktopMenu class="header__menu" :anchor-links="anchorLinks" />
	</header>
</template>

<style lang="scss" scoped>
	.header {
		margin: 1.25rem 0;
	}

	@media (width < 1440px) {
		.header {
			&__menu {
				display: none;
			}
		}
	}
</style>
