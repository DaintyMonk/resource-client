<script>
	import VTabBtn from "./v-tab-btn";
	import VIcon from "./v-icon";
	import VInfoEmptyIcon from "./icons/v-info-empty-icon";
	import VBtnSecondary from "./v-btn-secondary";
	export default {
		name: "VMenuModal",
		components: { VBtnSecondary, VInfoEmptyIcon, VIcon, VTabBtn },
		props: {
			itemType: {
				type: String,
				default: () => "",
			},
			img: {
				type: String,
				default: () => "",
			},
			name: {
				type: String,
				default: () => "",
			},
			description: {
				type: String,
				default: () => "",
			},
			price: {
				type: String,
				default: () => "",
			},
		},
		data() {
			return {
				sizes: [
					{
						char: "S",
						value: "200 ml",
					},
					{
						char: "M",
						value: "300 ml",
					},
					{
						char: "L",
						value: "400 ml",
					},
				],
				additives: ["Sugar", "Cinnamon", "Syrup"],
				currentSize: 0,
				currentAdditives: [0, 1, 2],
			};
		},
		mounted() {
			this.currentAdditives = Array(this.additives.length).fill(-1);
		},
		methods: {
			close() {
				this.$emit("close");
			},
			selectSize(id) {
				this.currentSize = id;
			},
			selectAdditives(id) {
				if (this.currentAdditives.includes(id)) {
					this.currentAdditives.splice(id, 1, -1);
				} else this.currentAdditives.splice(id, 1, id);
			},
		},
	};
</script>

<template>
	<transition name="modal-fade">
		<div class="modal-backdrop" role="dialog">
			<div ref="modal" class="modal">
				<div class="modal__img">
					<img
						:src="require(`~/assets/imgs/${itemType}/${img}.png`)"
						:alt="img"
					/>
				</div>
				<div class="modal__description">
					<div class="description__title">
						<h3 class="description__title-name heading-text heading-text_small">
							{{ name }}
						</h3>
						<p class="description__title-text main-text_medium">
							{{ description }}
						</p>
					</div>
					<div class="description__size">
						<p class="description__size-text">Size</p>
						<div class="description__size-tab">
							<VTabBtn
								v-for="(size, index) in sizes"
								:key="index"
								class="size__tab-item"
								:tab-name="size.value"
								:current-item-index="currentSize"
								:current-tab-index="index"
								@click.native="selectSize(index)"
								>{{ size.char }}</VTabBtn
							>
						</div>
					</div>
					<div class="description__additive">
						<p class="description__additive-text">Additives</p>
						<div class="description__additive-tab">
							<VTabBtn
								v-for="(additive, index) in additives"
								:key="index"
								class="additive__tab-item"
								:tab-name="additive"
								:current-item-index="currentAdditives[index]"
								:current-tab-index="index"
								@click.native="selectAdditives(index)"
								>{{ index + 1 }}
							</VTabBtn>
						</div>
					</div>
					<div class="description__total">
						<h3 class="description__total-text heading-text heading-text_small">
							Total
						</h3>
						<h3 class="description__total-text heading-text heading-text_small">
							{{ price }}
						</h3>
					</div>
					<div class="description__alert">
						<VIcon
							class="description__alert-icon"
							width="16"
							height="16"
							icon-color="transparent"
						>
							<VInfoEmptyIcon />
						</VIcon>
						<span class="description__alert-text main-text_caption">
							The cost is not final. Download our mobile app to see the final
							price and place your order. Earn loyalty points and enjoy your
							favorite coffee with up to 20% discount.</span
						>
					</div>
					<VBtnSecondary @click.native="close">Close</VBtnSecondary>
				</div>
			</div>
		</div>
	</transition>
</template>

<style lang="scss" scoped>
	.modal {
		display: flex;
		flex-wrap: wrap;
		background-color: var(--clr-200);
		padding: 1rem;
		border-radius: 2.5rem;

		&-backdrop {
			position: fixed;
			top: 0;
			bottom: 0;
			left: 0;
			right: 0;
			background-color: var(--clr-500);
			display: flex;
			justify-content: center;
			align-items: center;
			z-index: 1000;
		}

		&-fade-enter,
		&-fade-leave-active {
			opacity: 0;
		}

		&-fade-enter-active,
		&-fade-leave-active {
			transition: opacity 0.5s ease;
		}

		&__img {
			width: 19.375rem;
			height: 19.375rem;
			border: transparent;
			border-radius: 2.5rem;
			overflow: hidden;

			& > img {
				width: 100%;
				height: 100%;
				object-fit: cover;
				object-position: center;
			}
		}

		&__description {
			display: flex;
			flex-flow: column wrap;
			justify-content: space-between;
			width: 28.625rem;
			height: 29.5rem;
			padding: 0 0 0 1.25rem;
		}
	}

	.description {
		&__title,
		&__size,
		&__additive {
			&-name {
				margin: 0 0 0.75rem 0;
				color: var(--clr-700);
			}

			&-text {
				margin: 0;
				color: var(--clr-700);
			}

			&-tab {
				display: flex;
				margin-top: 0.5rem;
			}
		}

		&__total {
			display: flex;
			justify-content: space-between;

			&-text {
				margin: 0;
				color: var(--clr-700);
			}
		}

		&__alert {
			display: flex;
			padding: 0.75rem 0;
			border-top: 0.0625rem solid var(--clr-300);

			&-icon {
				margin-right: 0.5rem;
				stroke: var(--clr-700);
			}

			&-text {
				color: var(--clr-700);
			}
		}
	}

	.size__tab,
	.additive__tab {
		&-item {
			margin-right: 0.5rem;
		}
	}
</style>
