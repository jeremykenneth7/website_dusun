<script>
	import SectionWrapper from './SectionWrapper.svelte';
	const intro = 'Sambutan Dosen Pembimbing Lapangan';
	const nama = 'Isbandi Sutrisno, S.Sos, M.Si.';
	const jabatan = 'Dosen Pembimbing Lapangan';
	const sambutan = `
    <b>Assalamu'alaikum Warahmatullahi Wabarakatuh</b><br>
        Selamat datang di website Dusun Druju Tegal. 
        Saya sangat mengapresiasi semangat dan kerja keras seluruh tim KKN dalam membangun dan mengembangkan potensi desa ini.
        Semoga website ini dapat menjadi sarana informasi dan komunikasi yang bermanfaat bagi masyarakat dan pihak terkait.
        Teruslah berkarya dan berinovasi demi kemajuan bersama.
        Salam hangat dan sukses selalu untuk kita semua.
        <br><br>
        Hormat saya,<br>
        Isbandi Sutrisno, S.Sos, M.Si.
    `;
</script>

<SectionWrapper id="sambutan" class="pb-0">
	<div class="mx-23 mt-10 max-w-xl p-6">
		<h1 class="mb-2 text-4xl font-bold">{intro}</h1>
		<h2 class="mb-2 text-2xl font-bold">{nama}</h2>
		<h3 class="mb-2 text-lg text-gray-600">{jabatan}</h3>
		<div class="h-64 overflow-y-auto rounded bg-white" style="max-height: 16rem;">
			<div class="text-gray-800">{@html sambutan}</div>
		</div>
	</div>
</SectionWrapper>
