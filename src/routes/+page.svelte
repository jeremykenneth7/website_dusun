<script>
	import Administrasi from '../components/administrasi.svelte';
	import Dokumentasi from '../components/dokumentasi.svelte';
	import FloatingKunjungan from '../components/floating_kunjungan.svelte';
	import Hero from '../components/hero.svelte';
	import Komentar from '../components/komentar.svelte';
	import Map from '../components/map.svelte';
	import Map_2 from '../components/map_2.svelte';
	import Product from '../components/product.svelte';
	import Sambutan from '../components/sambutan.svelte';
	import StrukturDusun from '../components/struktur_dusun.svelte';
	import StrukturPemuda from '../components/struktur_pemuda.svelte';
</script>

<main class="flex w-full flex-col overflow-x-hidden">
	<Hero />
	<Sambutan />
	<Map />
	<Map_2 />
	<StrukturDusun />
	<StrukturPemuda />
	<Administrasi />
	<Product />
	<!-- <Potensi /> -->
	<Dokumentasi />
	<Komentar />
	<FloatingKunjungan />
</main>
