<script>
	import VIcon from "~/components/v-icon.vue";
	import VCoffeeCupIcon from "~/components/icons/v-coffee-cup-icon.vue";
	export default {
		name: "VDesktopMenu",
		components: { VCoffeeCupIcon, VIcon },
		props: {
			anchorLinks: {
				type: Array,
				default: () => [],
			},
		},
	};
</script>

<template>
	<div class="menu">
		<NuxtLink to="/">
			<img src="/header/logo.svg" alt="logo" width="100" height="60" />
		</NuxtLink>
		<nav class="menu__nav">
			<ul class="menu__nav-links" role="list">
				<li v-for="link in anchorLinks" :key="link.hash" class="menu__nav-item">
					<NuxtLink
						class="menu__nav-link link-text"
						:to="{ path: link.path, hash: link.hash }"
						>{{ link.text }}</NuxtLink
					>
				</li>
			</ul>
		</nav>
		<div class="menu__nav">
			<NuxtLink
				class="menu__nav-link link-text"
				to="/menu"
				active-class="menu__nav-link_active"
			>
				Menu
				<VIcon width="20" height="20" icon-color="none" stroke-color="none">
					<VCoffeeCupIcon />
				</VIcon>
			</NuxtLink>
		</div>
	</div>
</template>

<style lang="scss" scoped>
	@media (width >= 1440px) {
		.menu {
			display: flex;
			flex-wrap: wrap;
			justify-content: space-between;
			margin: 1.25rem 0;

			&__nav {
				margin-top: 1rem;

				&-links {
					display: flex;
					flex-wrap: wrap;
					margin: 0;
					padding: 0;
				}

				&-item {
					margin-inline: 1.25rem;

					&:last-child {
						margin-right: 0;
					}

					&:first-child {
						margin-left: 0;
					}
				}

				&-link {
					position: relative;
					color: var(--clr-700);

					> svg {
						fill: transparent;
						stroke: var(--clr-700);
					}

					&:after {
						content: "";
						position: absolute;
						left: 50%;
						transform: translateX(-50%);
						display: block;
						width: 0;
						height: 0.125rem;
						background-color: var(--clr-700);
						transition: width 0.3s ease-in-out;
					}

					&:hover:after,
					&_active:after {
						width: 100%;
					}

					> svg {
						display: inline-block;
						vertical-align: top;
						margin-left: 0.3125rem;
					}
				}
			}
		}
	}
</style>
