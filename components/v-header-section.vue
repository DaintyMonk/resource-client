<script lang="ts">
	import VIcon from "~/components/v-icon.vue";
	import VCoffeeCupIcon from "~/components/icons/v-coffee-cup-icon.vue";
	export default {
		name: "VHeaderSection",
		components: { VCoffeeCupIcon, VIcon },
	};
</script>

<template>
	<header class="header">
		<NuxtLink to="/">
			<img src="/header/logo.svg" alt="logo" width="100" height="60" />
		</NuxtLink>
		<nav>
			<ul class="anchor-links" role="list">
				<li class="anchor-links__item">
					<NuxtLink class="link" :to="{ path: '/', hash: 'favorite' }"
						>Favorite coffee</NuxtLink
					>
				</li>
				<li class="anchor-links__item">
					<NuxtLink class="link" :to="{ path: '/', hash: 'about' }"
						>About</NuxtLink
					>
				</li>
				<li class="anchor-links__item">
					<NuxtLink class="link" :to="{ path: '/', hash: 'mobile' }"
						>Mobile app</NuxtLink
					>
				</li>
				<li class="anchor-links__item">
					<NuxtLink class="link" :to="{ path: '/', hash: 'contact' }"
						>Contact us</NuxtLink
					>
				</li>
			</ul>
		</nav>
		<div class="menu-link">
			<NuxtLink class="link" to="/menu">
				Menu
				<VIcon width="20" height="20" icon-color="none" stroke-color="none">
					<VCoffeeCupIcon />
				</VIcon>
			</NuxtLink>
		</div>
	</header>
</template>

<style lang="scss" scoped>
	.header {
		display: flex;
		flex-wrap: wrap;
		justify-content: space-between;
		margin: 20px 0;
	}

	.anchor-links {
		display: flex;
		flex-wrap: wrap;
		margin: 1rem 0 0 0;
		padding: 0;

		&__item {
			margin-inline: 1.25rem;

			&:last-child {
				margin-right: 0;
			}

			&:first-child {
				margin-left: 0;
			}
		}
	}

	.menu-link {
		margin-top: 1rem;
	}

	.link {
		position: relative;
		font-size: var(--fs-300);
		font-weight: 600;
		line-height: 1.5;
		color: var(--clr-700);
		cursor: pointer;
		text-decoration: none;

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
			height: 2px;
			background-color: var(--clr-700);
			transition: width 0.3s ease-in-out;
		}

		&:hover:after,
		&:hover:focus {
			width: 100%;
		}

		> svg {
			display: inline-block;
			vertical-align: top;
			margin-left: 5px;
		}
	}
</style>
