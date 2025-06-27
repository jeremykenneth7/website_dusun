<script>
	import Sectionwrapper from './sectionwrapper.svelte';
	let productFeatures = [];
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
		<div class="relative grid grid-cols-1 gap-14 text-base md:grid-cols-2 md:gap-14 lg:gap-20">
			{#each productFeatures as feature}
				<div class="flex flex-col gap-4">
					<h4 class="text-lg font-semibold">{feature.title}</h4>
					<p class="text-gray-600">{feature.description}</p>
				</div>
			{/each}
		</div>
	</div>
</Sectionwrapper>
