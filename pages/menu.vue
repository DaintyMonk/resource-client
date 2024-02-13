<script>
	import VTabBtn from "../components/v-tab-btn";
	import VMenuCard from "../components/v-menu-card";
	import VBtnIconDark from "../components/v-btn-icon-dark";
	import VRefreshIcon from "../components/icons/v-refresh-icon";
	export default {
		name: "MenuPage",
		components: { VBtnIconDark, VRefreshIcon, VMenuCard, VTabBtn },
		data() {
			return {
				tabs: [
					{
						img: "coffee",
						tabName: "Coffee",
					},
					{
						img: "tea",
						tabName: "Tea",
					},
					{
						img: "dessert",
						tabName: "Dessert",
					},
				],
				coffees: [
					{
						id: 1,
						type: "coffee",
						img: "coffee-1",
						name: "Irish coffee",
						description:
							"Fragrant black coffee with Jameson Irish whiskey and whipped milk",
						price: "$7.00",
					},
					{
						id: 2,
						type: "coffee",
						img: "coffee-2",
						name: "Kahlua coffee",
						description:
							"Classic coffee with milk and Kahlua liqueur under a cap of frothed milk",
						price: "$7.00",
					},
					{
						id: 3,
						type: "coffee",
						img: "coffee-3",
						name: "Honey raf",
						description: "Espresso with frothed milk, cream and aromatic honey",
						price: "$5.50",
					},
					{
						id: 4,
						type: "coffee",
						img: "coffee-4",
						name: "Ice cappuccino",
						description:
							"Cappuccino with soft thick foam in summer version with ice",
						price: "$5.00",
					},
					{
						id: 5,
						type: "coffee",
						img: "coffee-5",
						name: "Espresso",
						description: "Classic black coffee",
						price: "$4.50",
					},
					{
						id: 6,
						type: "coffee",
						img: "coffee-6",
						name: "Latte",
						description:
							"Espresso coffee with the addition of steamed milk and dense milk foam",
						price: "$5.50",
					},
					{
						id: 7,
						type: "coffee",
						img: "coffee-7",
						name: "Latte macchiato",
						description: "Espresso with frothed milk and chocolate",
						price: "$5.50",
					},
					{
						id: 8,
						type: "coffee",
						img: "coffee-8",
						name: "Coffee with cognac",
						description: "Fragrant black coffee with cognac and whipped cream",
						price: "$6.50",
					},
				],
				teas: [
					{
						id: 1,
						type: "tea",
						img: "tea-1",
						name: "Moroccan",
						description:
							"Fragrant black tea with the addition of tangerine, cinnamon, honey, lemon and mint",
						price: "$4.50",
					},
					{
						id: 2,
						type: "tea",
						img: "tea-2",
						name: "Ginger",
						description:
							"Original black tea with fresh ginger, lemon and honey",
						price: "$5.00",
					},
					{
						id: 3,
						type: "tea",
						img: "tea-3",
						name: "Cranberry",
						description: "Invigorating black tea with cranberry and honey",
						price: "$5.00",
					},
					{
						id: 4,
						type: "tea",
						img: "tea-1",
						name: "Sea buckthorn",
						description:
							"Toning sweet black tea with sea buckthorn, fresh thyme and cinnamon",
						price: "$5.50",
					},
				],
				desserts: [
					{
						id: 1,
						type: "dessert",
						img: "dessert-1",
						name: "Marble cheesecake",
						description:
							"Philadelphia cheese with lemon zest on a light sponge cake and red currant jam",
						price: "$3.50",
					},
					{
						id: 2,
						type: "dessert",
						img: "dessert-2",
						name: "Red velvet",
						description: "Layer cake with cream cheese frosting",
						price: "$4.00",
					},
					{
						id: 3,
						type: "dessert",
						img: "dessert-3",
						name: "Cheesecakes",
						description:
							"Soft cottage cheese pancakes with sour cream and fresh berries and sprinkled with powdered sugar",
						price: "$4.50",
					},
					{
						id: 4,
						type: "dessert",
						img: "dessert-4",
						name: "Creme brulee",
						description:
							"Delicate creamy dessert in a caramel basket with wild berries",
						price: "$4.00",
					},
					{
						id: 5,
						type: "dessert",
						img: "dessert-5",
						name: "Pancakes",
						description:
							"Tender pancakes with strawberry jam and fresh strawberries",
						price: "$4.50",
					},
					{
						id: 6,
						type: "dessert",
						img: "dessert-6",
						name: "Honey cake",
						description: "Classic honey cake with delicate custard",
						price: "$4.50",
					},
					{
						id: 7,
						type: "dessert",
						img: "dessert-7",
						name: "Chocolate cake",
						description:
							"Cake with hot chocolate filling and nuts with dried apricots",
						price: "$5.50",
					},
					{
						id: 8,
						type: "dessert",
						img: "dessert-8",
						name: "Black forest",
						description:
							"A combination of thin sponge cake with cherry jam and light chocolate mousse",
						price: "$6.50",
					},
				],
				currentMenuIndex: 0,
			};
		},
		computed: {
			menu() {
				return [this.coffees, this.teas, this.desserts];
			},
		},
		methods: {
			selectMenu(id) {
				this.currentMenuIndex = id;
			},
		},
	};
</script>

<template>
	<section class="menu">
		<h2 class="menu__heading heading-text heading-text_medium">
			Behind each of our cups hides an
			<span class="text-accent">amazing surprise</span>
		</h2>
		<div class="menu__tab">
			<VTabBtn
				v-for="(tab, index) in tabs"
				:key="index"
				class="menu__tab-item"
				:tab-name="tab.tabName"
				:current-item-index="currentMenuIndex"
				:current-tab-index="index"
				@click.native="selectMenu(index)"
			>
				<img :src="require(`~/assets/imgs/emoji/${tab.img}.png`)" alt="" />
			</VTabBtn>
		</div>
		<div class="menu__container">
			<VMenuCard
				v-for="(card, index) in menu[currentMenuIndex]"
				:key="index"
				class="menu__container-card"
				:item-type="card.type"
				:img="card.img"
				:name="card.name"
				:description="card.description"
				:price="card.price"
			/>
		</div>
		<VBtnIconDark
			v-if="menu[currentMenuIndex].length > 4"
			class="menu__refresh"
		>
			<VRefreshIcon />
		</VBtnIconDark>
	</section>
</template>

<style lang="scss" scoped>
	.menu {
		margin-bottom: 6.25rem;

		&__heading {
			width: min(100%, 50rem);
			margin: 0 auto 2.5rem auto;
			text-align: center;
			color: var(--clr-700);
		}

		&__tab {
			display: flex;
			flex-wrap: wrap;
			justify-content: center;

			&-item {
				margin-inline: 0.5rem;
			}
		}

		&__container {
			display: flex;
			flex-flow: row wrap;
			justify-content: space-between;
			gap: 2.5rem;
			margin-top: 2.5rem;
		}

		&__refresh {
			display: none;
		}
	}

	@media (768px <= width < 1440px) {
		.menu {
			&__container {
				margin: 2.5rem 0.875rem;
			}

			&-item {
				&:nth-child(n + 5) {
					display: none;
				}
			}

			&__refresh {
				display: flex;
				margin-inline: auto;
			}
		}
	}

	@media (width < 768px) {
		.menu {
			&__container {
				flex-flow: column nowrap;
				justify-content: normal;
				margin: 2.5rem 1.1875rem;

				&-card {
					margin-inline: auto;
				}
			}

			&__tab {
				flex-wrap: nowrap;

				&-item {
					margin-inline: 0.25rem;
				}
			}

			&-item {
				&:nth-child(n + 5) {
					display: none;
				}
			}

			&__refresh {
				display: flex;
				margin-inline: auto;
			}
		}
	}
</style>
