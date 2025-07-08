<script>
	import { onMount } from 'svelte';
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

<div
	bind:this={mapDiv}
	style="height: 400px; width: 100%; max-width: 900px; margin: 1rem auto; border-radius: 12px;"
></div>
