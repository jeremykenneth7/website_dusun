<script>
	import Sectionwrapper from './sectionwrapper.svelte';
</script>

<Sectionwrapper id="potensi" class="pb-0">
	<div class="mx-4 flex max-w-4xl flex-col items-start px-2 sm:mx-18 sm:px-6">
		<h2 class="text-left text-3xl font-bold">POTENSI DUSUN</h2>
		<h3 class="mb-4 text-xl">
			Dusun Druju Tegal memiliki beberapa potensi unggulan, di antaranya:
		</h3>
		<div class="grid grid-cols-1 gap-8 md:grid-cols-2">
			<div class="flex flex-col items-center rounded-lg bg-white p-6 shadow-md">
				<img
					src="/potensi/slondok.jpg"
					alt="Slondok"
					class="mb-4 h-40 w-full rounded object-cover"
				/>
				<h4 class="mb-2 text-lg font-semibold">Slondok</h4>
				<p class="text-center text-gray-700">
					Slondok merupakan makanan ringan khas berbahan dasar singkong. Produk ini menjadi salah
					satu ikon kuliner Dusun Druju Tegal.
				</p>
			</div>
			<div class="flex flex-col items-center rounded-lg bg-white p-6 shadow-md">
				<img
					src="/potensi/kompos.jpeg"
					alt="Pupuk Kompos"
					class="mb-4 h-40 w-full rounded object-cover"
				/>
				<h4 class="mb-2 text-lg font-semibold">Pupuk Kompos</h4>
				<p class="text-center text-gray-700">
					Pupuk kompos dihasilkan dari residu pembakaran sampah oleh warga dusun. Pupuk Kompos ini
					dapat membantu untuk meningkatkan kualitas pertanian.
				</p>
			</div>
		</div>
	</div>
</Sectionwrapper>
