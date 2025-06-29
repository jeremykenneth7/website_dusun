<script>
	export let index;
	export let productFeature;
</script>

<div class="relative grid grid-cols-1 gap-14 text-base md:grid-cols-2 md:gap-14 lg:gap-20">
	<div class="flex flex-col gap-8 md:gap-10">
		<h4
			class="after:absoulte afther:h-1.5 relative w-full max-w-[1000px] text-2xl font-medium after:top-full after:left-0 after:mt-1 after:w-1/5 after:bg-slate-900 sm:text-3xl md:text-4xl"
		>
			<slot />
		</h4>
		<p>{productFeature.description}</p>
		<div class="flex flex-col gap-3">
			{#each productFeature.featureList as listitem}
				<div class="flex items-center gap-2">
					<div
						class="grid aspect-square place-items-center rounded-full border-[1.5px] border-solid border-green-300 bg-white px-1.5 text-xs sm:text-sm"
					>
						<i class="fa-solid fa-bolt text-green-400"></i>
					</div>
                    <p>{listitem}</p>
				</div>
			{/each}
		</div>
	</div>
</div>
