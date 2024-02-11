<script lang="ts">
	import VIcon from "~/components/v-icon.vue";
	import VTwitterIcon from "~/components/icons/v-twitter-icon.vue";
	import VInstagramIcon from "~/components/icons/v-instagram-icon.vue";
	import VFacebookIcon from "~/components/icons/v-facebook-icon.vue";
	import VPinIcon from "~/components/icons/v-pin-icon.vue";
	import VPhoneIcon from "~/components/icons/v-phone-icon.vue";
	import VClockIcon from "~/components/icons/v-clock-icon.vue";
	import VBtnIconLight from "~/components/v-btn-icon-light.vue";
	export default {
		name: "VSectionFooter",
		components: {
			VBtnIconLight,
			VClockIcon,
			VPhoneIcon,
			VPinIcon,
			VFacebookIcon,
			VInstagramIcon,
			VTwitterIcon,
			VIcon,
		},
	};
</script>

<template>
	<footer id="contact" class="footer">
		<div class="footer__social">
			<h2 class="social__heading heading-text heading-text_medium">
				Sip, Savor, Smile. <span class="text-accent">It’s coffee time!</span>
			</h2>
			<ul class="social__list" role="list">
				<li class="social__list-item">
					<VBtnIconLight class="social__button">
						<VTwitterIcon />
					</VBtnIconLight>
				</li>
				<li class="social__list-item">
					<VBtnIconLight class="social__button">
						<VInstagramIcon />
					</VBtnIconLight>
				</li>
				<li class="social__list-item">
					<VBtnIconLight class="social__button">
						<VFacebookIcon />
					</VBtnIconLight>
				</li>
			</ul>
		</div>
		<div class="footer__contacts">
			<h3 class="contacts__heading heading-text heading-text_small">
				Contact us
			</h3>
			<nav>
				<ul class="contacts__list" role="list">
					<li class="contacts__list-item">
						<NuxtLink class="contacts__link" to="/">
							<VIcon
								class="contacts__link-icon"
								width="20"
								height="20"
								icon-color="transparent"
								stroke-color="none"
							>
								<VPinIcon />
							</VIcon>
							8558 Green Rd., LA
						</NuxtLink>
					</li>
					<li class="contacts__list-item">
						<NuxtLink class="contacts__link" to="/">
							<VIcon
								class="contacts__link-icon"
								width="20"
								height="20"
								icon-color="transparent"
								stroke-color="none"
							>
								<VPhoneIcon />
							</VIcon>
							+1 (603) 555-0123
						</NuxtLink>
					</li>
					<li class="contacts__list-item">
						<span class="contacts__link">
							<VIcon
								class="contacts__link-icon"
								width="20"
								height="20"
								icon-color="transparent"
								stroke-color="none"
							>
								<VClockIcon />
							</VIcon>
							Mon-Sat: 9:00 AM – 23:00 PM
						</span>
					</li>
				</ul>
			</nav>
		</div>
	</footer>
</template>

<style lang="scss" scoped>
	.footer {
		display: flex;
		flex-wrap: wrap;
		align-items: center;
		justify-content: space-between;
		margin-bottom: 2.5rem;
		padding: 6.25rem;
		background-color: var(--clr-600);
		border-radius: 2.5rem;

		&__social {
			width: min(100%, 33.13rem);
		}

		&__contacts {
			width: min(100%, 33.13rem);
		}
	}

	.social {
		&__heading {
			margin: 0 0 2.5rem 0;
			color: var(--clr-200);
		}

		&__list {
			display: flex;
			flex-wrap: wrap;
			margin: 0;
			padding: 0;
			gap: 0.75rem;
		}
	}

	.contacts {
		&__heading {
			margin: 0 0 2.5rem 0;
			color: var(--clr-200);
		}

		&__list {
			margin: 0;
			padding: 0;
		}

		&__list-item {
			margin-bottom: 1.25rem;

			&:last-child {
				margin-bottom: 0;
			}
		}

		&__link {
			position: relative;
			font-size: var(--fs-300);
			font-weight: var(--fw-bold);
			line-height: 1.5;
			color: var(--clr-200);
			text-decoration: none;

			&:after {
				content: "";
				position: absolute;
				left: 50%;
				transform: translateX(-50%);
				display: block;
				width: 0;
				height: 0.125rem;
				background-color: var(--clr-200);
				transition: width 0.3s ease-in-out;
			}

			&:hover:after,
			&:hover:focus {
				width: 100%;
			}

			&:is(span):hover:after {
				width: 0;
			}

			&-icon {
				margin-right: 0.3rem;
				display: inline-block;
				vertical-align: top;
				stroke: var(--clr-200);
			}
		}
	}
</style>
