<script>
	import Sectionwrapper from './sectionwrapper.svelte';
	const stats = [
		{
			label: 'Penduduk',
			value: '1.890',
			img: 'https://cdn.digitaldesa.com/statics/profil-v2/assets/total-penduduk-CXnnuYJa.png'
		},
		{
			label: 'Laki-Laki',
			value: '930',
			img: 'https://cdn.digitaldesa.com/statics/profil-v2/assets/laki-qsjhxY_S.png'
		},
		{
			label: 'Kepala Keluarga',
			value: '436',
			img: 'https://cdn.digitaldesa.com/statics/profil-v2/assets/kepala-keluarga-BcdRTpvQ.png'
		},
		{
			label: 'Perempuan',
			value: '960',
			img: 'https://cdn.digitaldesa.com/statics/profil-v2/assets/perempuan-CSZtJeWt.png'
		},
		{
			label: 'Penduduk Sementara',
			value: '0',
			img: 'https://cdn.digitaldesa.com/statics/profil-v2/assets/penduduk-sementara-P644cOda.png'
		},
		{
			label: 'Mutasi Penduduk',
			value: '2',
			img: 'https://cdn.digitaldesa.com/statics/profil-v2/assets/mutasi-penduduk-_1rO7gmp.png'
		}
	];
</script>

<Sectionwrapper id="administrasi" class="pb-0">
	<div class="admin-container">
		<div class="mx-4 flex max-w-4xl flex-col items-start px-2 sm:mx-18 sm:px-6">
			<h2 class="text-left text-2xl font-bold sm:text-3xl">ADMINISTRASI PENDUDUK</h2>
			<h3 class="mb-2 text-left text-base sm:text-xl">
				Beberapa data administrasi penduduk yang berada di Dusun Druju Tegal.
				<br />
				Data ini diambil dari data kependudukan yang dikelola oleh Pemerintah Desa.
			</h3>
		</div>
		<div class="admin-grid mx-0 sm:mx-22">
			{#each stats as stat}
				<div class="admin-card">
					<img src={stat.img} alt={stat.label} />
					<div class="admin-card-value">{stat.value}</div>
					<div class="admin-card-label">{stat.label}</div>
				</div>
			{/each}
		</div>
	</div>
</Sectionwrapper>

<style>
	.admin-container {
		display: flex;
		flex-direction: column;
		gap: 2rem;
	}
	.admin-grid {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
		gap: 1.5rem;
	}
	.admin-card {
		background: #fff;
		border-radius: 1rem;
		box-shadow: 0 2px 8px rgba(0, 0, 0, 0.07);
		padding: 1.5rem 1rem;
		display: flex;
		flex-direction: column;
		align-items: center;
		gap: 0.5rem;
	}
	.admin-card img {
		width: 50px;
	}
	.admin-card-value {
		font-size: 2rem;
		font-weight: 800;
		color: #1971c2;
		margin-bottom: 0.25rem;
	}
	.admin-card-label {
		font-size: 1rem;
		color: #555;
		text-align: center;
	}
	@media (max-width: 600px) {
		.admin-grid {
			grid-template-columns: 1fr 1fr;
		}
	}
</style>
