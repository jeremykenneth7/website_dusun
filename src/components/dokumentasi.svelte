<script>
	import Sectionwrapper from './sectionwrapper.svelte';
	import 'keen-slider/keen-slider.min.css';
	import { onMount } from 'svelte';
	let dokumentasi = [
		{ src: '/dokumentasi/photo_1.jpg', caption: 'Colouring Day' },
		{ src: '/dokumentasi/photo_2.jpg', caption: 'Rapat Bersama Warga' },
		{ src: '/dokumentasi/photo_3.jpeg', caption: 'Penyambutan Haji' },
		{ src: '/dokumentasi/photo_2.jpg', caption: 'Kerja Bakti' },
		{ src: '/dokumentasi/photo_2.jpg', caption: 'Kegiatan 5' },
		{ src: '/dokumentasi/photo_2.jpg', caption: 'Kerja Bakti' },
		{ src: '/dokumentasi/photo_2.jpg', caption: 'Kegiatan 5' },
		{ src: '/dokumentasi/photo_2.jpg', caption: 'Kerja Bakti' },
		{ src: '/dokumentasi/photo_2.jpg', caption: 'Kegiatan 5' }
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
	<div class="mx-4 flex max-w-4xl flex-col items-start px-2 sm:mx-18 sm:px-6">
		<h2 class="mb-1 text-left text-2xl font-bold sm:text-3xl">DOKUMENTASI KEGIATAN DUSUN</h2>
		<h3 class="mb-2 text-left text-base sm:text-xl">
			Beberapa dokumentasi kegiatan yang berada di Dusun Druju Tegal.
		</h3>
	</div>

	<div class="container mx-0 sm:mx-22">
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
