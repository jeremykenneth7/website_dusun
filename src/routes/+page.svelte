<script>
	import Administrasi from '../components/administrasi.svelte';
	import Dokumentasi from '../components/dokumentasi.svelte';
	import FloatingKunjungan from '../components/floating_kunjungan.svelte';
	import Hero from '../components/hero.svelte';
	import Komentar from '../components/komentar.svelte';
	import Map from '../components/map.svelte';
	import Map_2 from '../components/map_2.svelte';
	import Potensi from '../components/potensi.svelte';
	import Product from '../components/product.svelte';
	import Sambutan from '../components/sambutan.svelte';
	import StrukturDusun from '../components/struktur_dusun.svelte';
	import StrukturPemuda from '../components/struktur_pemuda.svelte';
</script>

<main class="flex flex-col">
	<Hero />
	<Sambutan />
	<Map />
	<Map_2 />
	<StrukturDusun />
	<StrukturPemuda />
	<Administrasi />
	<Potensi />
	<Dokumentasi />
	<Komentar />
	<FloatingKunjungan />
</main>
