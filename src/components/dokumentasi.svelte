<script>
	import SectionWrapper from './SectionWrapper.svelte';
	import 'keen-slider/keen-slider.min.css';
	import { onMount } from 'svelte';
	let dokumentasi = [
		{ src: '/dokumentasi/photo_1.jpg', caption: 'Kegiatan 1' },
		{ src: '/dokumentasi/photo_2.jpg', caption: 'Kegiatan 2' },
		{ src: '/dokumentasi/photo_2.jpg', caption: 'Kegiatan 3' },
		{ src: '/dokumentasi/photo_2.jpg', caption: 'Kegiatan 4' },
		{ src: '/dokumentasi/photo_2.jpg', caption: 'Kegiatan 5' }
	];

	let slider;
	let sliderRef;

	onMount(async () => {
		const KeenSlider = (await import('keen-slider')).default;
		slider = new KeenSlider(sliderRef, {
			slides: { perView: 3, spacing: 16 },
			loop: true
		});
		return () => slider.destroy();
	});
</script>

<SectionWrapper id="dokumentasi" class="pb-0">
	<div class="mx-18 max-w-xl px-8">
		<h2 class="mt-2 text-left text-3xl font-bold">DOKUMENTASI KKN</h2>
		<h3 class="mb-2 text-left text-xl">Beberapa dokumentasi kegiatan KKN di Dusun Druju Tegal.</h3>
	</div>

	<div class="container mx-22">
		<div bind:this={sliderRef} class="keen-slider mb-8">
			{#each dokumentasi as item}
				<div class="keen-slider__slide">
					<div class="p-2">
						<img
							src={item.src}
							alt={item.caption}
							class="h-48 w-full rounded-lg object-cover shadow-md"
						/>
						<div class="mt-2 text-center text-sm">{item.caption}</div>
					</div>
				</div>
			{/each}
		</div>
	</div>
</SectionWrapper>
