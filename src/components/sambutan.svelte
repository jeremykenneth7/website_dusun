<script>
	import SectionWrapper from './SectionWrapper.svelte';
	const intro = 'Sambutan Kepala Dusun Druju Tegal';
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

<SectionWrapper id="sambutan" class="pb-0">
    <div class="mx-18 mt-16 flex max-w-4xl items-start gap-12 px-6">
        <!-- Logo Dusun -->
        <img src="/logo/logo_dusun.png" alt="Logo Dusun" class="h-1/3 w-1/3 rounded object-contain" />

        <!-- Sambutan -->
        <div>
            <h1 class="mb-2 text-4xl font-bold">{intro}</h1>
            <h2 class="mb-2 text-2xl font-bold">{nama}</h2>
            <h3 class="mb-2 text-lg text-gray-600">{jabatan}</h3>
            <div class="h-64 overflow-y-auto rounded bg-white" style="max-height: 10rem;">
                <div class="text-gray-800">{@html sambutan}</div>
            </div>
        </div>
    </div>
</SectionWrapper>
