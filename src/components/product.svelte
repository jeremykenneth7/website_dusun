<script>
	import ProductCard from './product_card.svelte';
	import Sectionwrapper from './sectionwrapper.svelte';
	let productFeatures = [
		{
			featureList: ['Feature 1', 'Feature 2', 'Feature 3', 'Feature 4'],
			description:
				'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.',
			imgUrl: 'https://via.placeholder.com/150'
		},
		{
			featureList: ['Feature 1', 'Feature 2', 'Feature 3', 'Feature 4'],
			description:
				'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.',
			imgUrl: 'https://via.placeholder.com/150'
		},
		{
			featureList: ['Feature 1', 'Feature 2', 'Feature 3', 'Feature 4'],
			description:
				'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.',
			imgUrl: 'https://via.placeholder.com/150'
		}
	];
</script>

<Sectionwrapper id="product">
	<div
		class="flex flex-1 flex-col items-center justify-center gap-10 pb-10 sm:gap-14 md:gap-24 md:pb-14"
	>
		<div class="flex flex-col gap-2">
			<p class="text-center text-base opacity-60 sm:text-lg md:text-xl">
				Test <span class="text-indigo-400">Testtttt</span>
			</p>
			<h3
				class="mx-auto w-full max-w-[1000px] text-center text-4xl font-semibold sm:text-5xl md:text-6xl"
			>
				<span class="text-indigo-400">Test</span> Product
			</h3>
		</div>
		{#each productFeatures as productFeature, index}
			<ProductCard {productFeature} {index}>
				{#if index === 0}
				Example Product 1 <span class="text-indigo-400">Test</span>
				{:else if index === 3}
				{:else if index === 2}
				Example Product 3
				{:else if index === 1}
				Example Product 2
				{:else}
				Example Product 2
				{/if}
			</ProductCard>
		{/each}
	</div>
</Sectionwrapper>
