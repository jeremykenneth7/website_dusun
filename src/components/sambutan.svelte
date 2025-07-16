<script>
	import Sectionwrapper from './sectionwrapper.svelte';
	const intro = 'SAMBUTAN KEPALA DUSUN DRUJU TEGAL';
	const nama = 'Mukhlis Arifin';
	const jabatan = 'Kepala Dusun Druju Tegal';
	const sambutan = `
    <b>Assalamu'alaikum Warahmatullahi Wabarakatuh</b><br>
		Selamat datang di website resmi Dusun Druju Tegal. Website ini dibuat sebagai sarana informasi dan komunikasi bagi warga dusun kami. Kami berharap dengan adanya website ini, informasi mengenai kegiatan, produk, peta, dan potensi yang ada di Dusun Druju Tegal dapat lebih mudah diakses oleh masyarakat luas.<br>
        <br>
        <b>Kepala Dusun Druju Tegal<br>
        Mukhlis Arifin</b>
    `;
</script>

<Sectionwrapper id="sambutan" class="pb-0">
	<div
		class="mx-4 flex max-w-4xl flex-col items-start gap-2 px-2 sm:mx-18 sm:mt-16 sm:flex-row sm:gap-12 sm:px-6"
	>
		<img
			src="/logo/logo_dusun.png"
			alt="Logo Dusun"
			class="h-32 w-32 rounded object-contain sm:h-1/3 sm:w-1/3"
		/>
		<div>
			<h1 class="text-2xl font-bold sm:text-4xl">{intro}</h1>
			<h2 class="text-lg font-bold sm:text-2xl">{nama}</h2>
			<h3 class="mb-3 text-base text-gray-600 sm:text-lg">{jabatan}</h3>
			<div
				class="h-40 overflow-y-scroll rounded bg-white sm:h-64"
				style="max-height: 10rem; scrollbar-width: auto; scrollbar-color: #a0aec0 #edf2f7;"
			>
				<div class="text-gray-800">{@html sambutan}</div>
			</div>
		</div>
	</div>
</Sectionwrapper>
