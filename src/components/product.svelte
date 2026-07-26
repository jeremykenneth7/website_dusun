<script>
	import Sectionwrapper from './sectionwrapper.svelte';
	import ProductCard from './product_card.svelte';

	const whatsappNumbers = ['088299606749', '085813430977', '082314528822'];

	function pickRandomWhatsApp() {
		const randomIndex = Math.floor(Math.random() * whatsappNumbers.length);
		return whatsappNumbers[randomIndex];
	}

	const products = [
		{
			title: 'Pupuk Kompos',
			img: '/potensi/kompos.jpeg',
			href: 'https://wa.me/6282329082780?text=Halo%20saya%20tertarik%20dengan%20Pupuk%20Kompos',
			feature: {
				description: 'Pupuk kompos organik hasil olahan warga Dusun Druju Tegal.',
				featureList: ['Ramah lingkungan', 'Meningkatkan kesuburan tanah', 'Tersedia dalam berbagai ukuran']
			}
		},
		{
			title: 'Slondok',
			img: '/potensi/slondok.jpg',
			href: `https://wa.me/${pickRandomWhatsApp()}?text=Halo%20saya%20tertarik%20dengan%20Selondok`,
			feature: {
				description: 'Produk lokal yang terbuat dari bahan alami dan ramah lingkungan.',
				featureList: ['Bahan alami', 'Tersedia dalam berbagai ukuran', 'Varian rasa yang menarik']
			}
		}
	];
</script>

<Sectionwrapper id="product" class="pb-0">
	<div class="flex w-full flex-col items-start px-2 sm:px-6 lg:px-8">
		<h2 class="text-left text-3xl font-bold">BELI DARI DUSUN</h2>
		<h3 class="mb-4 text-xl">
			Layanan yang disediakan promosi produk UMKM Dusun sehingga mampu meningkatkan perekonomian
			masyarakat Dusun Druju Tegal.
		</h3>

		<div class="grid grid-cols-1 gap-8 md:grid-cols-2 lg:grid-cols-3 w-full">
			{#each products as p}
				<ProductCard title={p.title} imgSrc={p.img} href={p.href} productFeature={p.feature} />
			{/each}
		</div>
	</div>
</Sectionwrapper>
