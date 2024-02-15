<script>
	import VCoffeeCupIcon from "~/components/icons/v-coffee-cup-icon";
	import VIcon from "~/components/v-icon";
	import VBtnBurger from "~/components/v-btn-burger";

	export default {
		name: "VBurgerMenu",
		components: { VBtnBurger, VCoffeeCupIcon, VIcon },
		props: {
			anchorLinks: {
				type: Array,
				default: () => [],
			},
		},
		data() {
			return {
				open: false,
			};
		},
		computed: {
			state() {
				if (this.open) return "burger-menu__nav_active";
				else return "";
			},
		},
		methods: {
			changeState() {
				this.open = !this.open;
			},
		},
	};
</script>

<template>
	<div class="burger-menu">
		<div class="burger-menu__panel">
			<NuxtLink to="/">
				<img src="/header/logo.svg" alt="logo" width="100" height="60" />
			</NuxtLink>
			<VBtnBurger @click.native="changeState" />
		</div>
		<nav class="burger-menu__nav" :class="state">
			<ul class="burger-menu__nav-links" role="list">
				<li
					v-for="link in anchorLinks"
					:key="link.hash"
					class="burger-menu__nav-item"
				>
					<NuxtLink
						class="burger-menu__nav-link burger-link"
						:to="{ path: link.path, hash: link.hash }"
						>{{ link.text }}</NuxtLink
					>
				</li>
			</ul>
			<NuxtLink
				class="burger-menu__coffee-menu burger-menu__nav-link burger-link"
				to="/menu"
				active-class="burger-menu__nav-link_active"
			>
				Menu
				<VIcon icon-color="transparent" stroke-color="none">
					<VCoffeeCupIcon />
				</VIcon>
			</NuxtLink>
		</nav>
	</div>
</template>

<style lang="scss" scoped>
	@media (width < 1440px) {
		.burger-menu {
			display: flex;
			flex-direction: column;

			&__panel {
				display: flex;
				align-items: center;
				justify-content: space-between;
				margin: 1.25rem 0;
			}

			&__nav {
				display: none;
				flex-direction: column;
				align-items: center;
				height: 57.75rem;
				padding: 3.75rem 2.5rem;

				&-links {
					display: flex;
					flex-direction: column;
					align-items: center;
					justify-content: space-between;
					flex-wrap: wrap;
					height: 21.25rem;
					margin: 0;
					padding: 0;
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
						width: 2.3rem;
						height: 2.3rem;
						display: inline-block;
						vertical-align: top;
						margin-left: 0.3125rem;
					}
				}

				&_active {
					display: flex;
				}
			}

			&__coffee-menu {
				margin-top: 6.25rem;
			}
		}
	}

	@media (width < 768px) {
		.burger-menu {
			&__nav {
				height: 45.25rem;
				padding-inline: 1rem;

				&-links {
					height: 21.25rem;
				}
			}
		}
	}
</style>
