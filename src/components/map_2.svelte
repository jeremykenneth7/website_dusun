<script>
	import { onMount } from 'svelte';
	import Sectionwrapper from './sectionwrapper.svelte';
	let mapDiv;
	let map;

	onMount(async () => {
		if (typeof window !== 'undefined') {
			const L = (await import('leaflet')).default;
			map = L.map(mapDiv).setView([-7.631072, 110.269306], 15);

			L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
				attribution: '&copy; KKN AA.83.023'
			}).addTo(map);
		}
	});

	export { map };
</script>

<Sectionwrapper id="map2" class="pb-0">
	<div class="mx-4 flex max-w-4xl flex-col items-start px-2 sm:mx-18 sm:px-6">
		<h2 class="mt-2 text-left text-3xl font-bold">PETA RAWAN BENCANA DUSUN DRUJU TEGAL</h2>
		<h3 class="text-left text-xl">
			Peta yang menampilkan data rawan bencana dan mitigasinya yang berada di Dusun Druju Tegal.
		</h3>
		<div
			bind:this={mapDiv}
			style="height: 400px; width: 100%; border-radius: 12px; margin-top: 1rem;"
		></div>
	</div>
</Sectionwrapper>
