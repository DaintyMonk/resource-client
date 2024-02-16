<script>
	import VCoffeeCupIcon from "~/components/icons/v-coffee-cup-icon";
	import VIcon from "~/components/v-icon";
	import VBtnBurger from "~/components/v-btn-burger";

	export default {
		name: "VSectionHeader",
		components: { VBtnBurger, VCoffeeCupIcon, VIcon },
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
				open: false,
			};
		},
	};
</script>

<template>
	<header class="header">
		<div class="header__panel">
			<NuxtLink to="/">
				<img src="/header/logo.svg" alt="logo" width="100" height="60" />
			</NuxtLink>
			<nav class="panel__nav-menu">
				<ul class="nav-menu__links" role="list">
					<li
						v-for="link in anchorLinks"
						:key="link.hash"
						class="nav-menu__item"
					>
						<NuxtLink
							class="header__link link-text"
							:to="{ path: link.path, hash: link.hash }"
							>{{ link.text }}</NuxtLink
						>
					</li>
				</ul>
			</nav>
			<div class="panel__nav-menu">
				<NuxtLink
					class="header__link link-text"
					to="/menu"
					active-class="header__link_active"
				>
					Menu
					<VIcon width="20" height="20" icon-color="none" stroke-color="none">
						<VCoffeeCupIcon />
					</VIcon>
				</NuxtLink>
			</div>
			<VBtnBurger
				class="panel__burger-btn"
				:open="open"
				@click.native="open = !open"
			/>
		</div>
		<transition name="menu-fade">
			<nav v-if="open" class="header__burger-menu">
				<ul class="burger-menu__nav-links" role="list">
					<li
						v-for="link in anchorLinks"
						:key="link.hash"
						class="burger-menu__nav-item"
					>
						<NuxtLink
							class="header__link burger-link"
							:to="{ path: link.path, hash: link.hash }"
							@click.native="open = !open"
							>{{ link.text }}</NuxtLink
						>
					</li>
				</ul>
				<NuxtLink
					class="burger-menu__link header__link burger-link"
					to="/menu"
					active-class="header__link_active"
					@click.native="open = !open"
				>
					Menu
					<VIcon icon-color="transparent" stroke-color="none">
						<VCoffeeCupIcon />
					</VIcon>
				</NuxtLink>
			</nav>
		</transition>
	</header>
</template>

<style lang="scss" scoped>
	.header {
		&__panel {
			display: flex;
			flex-wrap: wrap;
			justify-content: space-between;
			margin: 1.25rem 0;
		}

		&__link {
			position: relative;
			color: var(--clr-700);

			> svg {
				display: inline-block;
				vertical-align: top;
				margin-left: 0.3125rem;
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
		}
	}

	.panel {
		&__nav-menu {
			margin-top: 1rem;
		}

		&__burger-btn {
			display: none;
		}
	}

	.nav-menu {
		&__links {
			display: flex;
			flex-wrap: wrap;
			margin: 0;
			padding: 0;
		}

		&__item {
			margin-inline: 1.25rem;
		}
	}

	@media (width < 1440px) {
		.header {
			&__panel {
				position: relative;
				align-items: center;
			}

			&__burger-menu {
				position: absolute;
				left: 0;
				z-index: 1;
				display: flex;
				flex-direction: column;
				align-items: center;
				width: 100%;
				padding: 3.75rem 2.5rem;
				background-color: var(--clr-200);
			}

			&__link {
				> svg {
					width: 2.3rem;
					height: 2.3rem;
				}
			}
		}

		.panel {
			&__nav-menu {
				display: none;
			}

			&__burger-btn {
				display: flex;
			}
		}

		.burger-menu {
			&__nav-links {
				display: flex;
				flex-direction: column;
				align-items: center;
				justify-content: space-between;
				flex-wrap: wrap;
				height: 21.25rem;
				margin: 0;
				padding: 0;
			}

			&__link {
				margin-top: 6.25rem;
			}
		}

		.menu-fade {
			&-enter-active {
				transition: transform 0.5s ease-in-out;
			}

			&-leave-active {
				transition: transform 0.2s ease-in-out;
			}

			&-enter,
			&-leave-to {
				transform: translateX(100%);
			}
		}
	}

	@media (768px <= width < 1440px) {
		.header {
			&__burger-menu {
				height: 57.75rem;
				padding: 3.75rem 2.5rem;
			}
		}
	}

	@media (width < 768px) {
		.header {
			&__burger-menu {
				height: 45.25rem;
				padding-inline: 1rem;
			}
		}
	}
</style>
