<script lang="ts">
	import VDesktopMenu from "~/components/v-desktop-menu.vue";
	import VBurgerMenu from "~/components/v-burger-menu.vue";
	export default {
		name: "VSectionHeader",
		components: { VBurgerMenu, VDesktopMenu },
		data() {
			return {
				anchorLinks: [
					{
						path: "/",
						hash: "favorite",
						text: "Favorite coffee",
					},
					{
						path: "/",
						hash: "about",
						text: "About",
					},
					{
						path: "/",
						hash: "mobile",
						text: "Mobile app",
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
		<VBurgerMenu class="header__burger-menu" :anchor-links="anchorLinks" />
	</header>
</template>

<style lang="scss" scoped>
	.header {
		&__burger-menu {
			display: none;
		}
	}

	@media (width < 1440px) {
		.header {
			&__menu {
				display: none;
			}

			&__burger-menu {
				display: block;
			}
		}
	}
</style>
