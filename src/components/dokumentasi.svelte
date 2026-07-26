<script>
	import Sectionwrapper from './sectionwrapper.svelte';
	import 'keen-slider/keen-slider.min.css';
	import { onMount } from 'svelte';
	let dokumentasi = [
		{ src: '/dokumentasi/posyandu_2026.jpeg', caption: 'Posyandu' },
		{ src: '/dokumentasi/senam_2026.jpeg', caption: 'Senam Pagi' },
		{ src: '/dokumentasi/kerja_bakti_2026.jpeg', caption: 'Kerja Bakti' },
		{ src: '/dokumentasi/dawis_2026.jpeg', caption: 'Dasawisma' },
	];

	let slider;
	let sliderRef;

	onMount(async () => {
		const KeenSlider = (await import('keen-slider')).default;
		slider = new KeenSlider(sliderRef, {
			breakpoints: {
				'(max-width: 640px)': {
					slides: { perView: 2, spacing: 2 }
				}
			},
			slides: { perView: 3, spacing: 16 },
			loop: true
		});
		return () => slider.destroy();
	});
</script>

<Sectionwrapper id="dokumentasi" class="pb-0">
	<div class="flex w-full flex-col items-start px-2 sm:px-6 lg:px-8">
		<h2 class="mb-1 text-left text-2xl font-bold sm:text-3xl">DOKUMENTASI KEGIATAN DUSUN</h2>
		<h3 class="mb-2 text-left text-base sm:text-xl">
			Beberapa dokumentasi kegiatan yang berada di Dusun Druju Tegal.
		</h3>
	</div>

	<div class="w-full px-2 sm:px-6 lg:px-8">
		<div bind:this={sliderRef} class="keen-slider">
			{#each dokumentasi as item}
				<div class="keen-slider__slide">
					<div class="p-1 sm:p-2">
						<img
							src={item.src}
							alt={item.caption}
							class="h-40 w-full rounded-lg object-cover shadow-md sm:h-48"
						/>
						<div class="mt-2 text-center text-xs sm:text-sm">{item.caption}</div>
					</div>
				</div>
			{/each}
		</div>
	</div>
</Sectionwrapper>
