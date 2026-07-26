<script>
	export let productFeature = { description: '', featureList: [] };
	export let title = '';
	export let imgSrc = '';
	export let href = '#';
</script>

<div class="flex flex-col items-center rounded-lg bg-white p-6 shadow-md transition hover:shadow-lg">
	<a
		href={href}
		target="_blank"
		rel="noopener noreferrer"
		class="flex flex-col items-center w-full"
	>
		{#if imgSrc}
			<img src={imgSrc} alt={title} class="mb-4 h-40 w-full rounded object-cover" />
		{/if}
		<h4 class="mb-4 text-lg font-semibold">{title}</h4>
	</a>

	<div class="w-full text-left">
		{#if productFeature.description}
			<p class="text-sm text-gray-700">{productFeature.description}</p>
		{/if}

		{#if productFeature.featureList && productFeature.featureList.length}
			<div class="flex flex-col gap-3 mt-3">
				{#each productFeature.featureList as listitem}
					<div class="flex items-center gap-2">
						<div
							class="grid aspect-square place-items-center rounded-full border-[1.5px] border-solid border-green-300 bg-white px-1.5 text-xs sm:text-sm"
						>
							<i class="fa-solid fa-check text-green-600" aria-hidden="true"></i>
						</div>
						<p class="text-sm">{listitem}</p>
					</div>
				{/each}
			</div>
		{/if}
	</div>
</div>
