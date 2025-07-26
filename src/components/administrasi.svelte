<script>
	import Sectionwrapper from './sectionwrapper.svelte';
	import { onMount } from 'svelte';
	import { initializeApp } from 'firebase/app';
	import { getDatabase, ref, set, onValue } from 'firebase/database';

	const firebaseConfig = {
		apiKey: import.meta.env.VITE_FIREBASE_API_KEY,
		authDomain: import.meta.env.VITE_FIREBASE_AUTH_DOMAIN,
		projectId: import.meta.env.VITE_FIREBASE_PROJECT_ID,
		storageBucket: import.meta.env.VITE_FIREBASE_STORAGE_BUCKET,
		messagingSenderId: import.meta.env.VITE_FIREBASE_MESSAGING_SENDER_ID,
		appId: import.meta.env.VITE_FIREBASE_APP_ID,
		measurementId: import.meta.env.VITE_FIREBASE_MEASUREMENT_ID,
		databaseURL: import.meta.env.VITE_FIREBASE_DATABASE_URL
	};

	const app = initializeApp(firebaseConfig);
	const db = getDatabase(app);

	let stats = [
		{
			label: 'Penduduk',
			value: '464',
			img: 'https://cdn.digitaldesa.com/statics/profil-v2/assets/total-penduduk-CXnnuYJa.png'
		},
		{
			label: 'Laki-Laki',
			value: '217',
			img: 'https://cdn.digitaldesa.com/statics/profil-v2/assets/laki-qsjhxY_S.png'
		},
		{
			label: 'Kepala Keluarga',
			value: '150',
			img: 'https://cdn.digitaldesa.com/statics/profil-v2/assets/kepala-keluarga-BcdRTpvQ.png'
		},
		{
			label: 'Perempuan',
			value: '247',
			img: 'https://cdn.digitaldesa.com/statics/profil-v2/assets/perempuan-CSZtJeWt.png'
		},
		{
			label: 'Penduduk Sementara',
			value: '0',
			img: 'https://cdn.digitaldesa.com/statics/profil-v2/assets/penduduk-sementara-P644cOda.png'
		},
		{
			label: 'Mutasi Penduduk',
			value: '0',
			img: 'https://cdn.digitaldesa.com/statics/profil-v2/assets/mutasi-penduduk-_1rO7gmp.png'
		}
	];

	let isAdmin = false;
	let editMode = false;
	let editedStats = [];

	onMount(() => {
		isAdmin = localStorage.getItem('isAdmin') === 'true';

		const statsRef = ref(db, 'administrasi');
		onValue(statsRef, (snapshot) => {
			const data = snapshot.val();
			if (data) {
				stats = data;
			}
		});
	});

	function startEdit() {
		editedStats = JSON.parse(JSON.stringify(stats));
		editMode = true;
	}

	function cancelEdit() {
		editMode = false;
	}

	function saveEdit() {
		const statsRef = ref(db, 'administrasi');
		set(statsRef, editedStats);
		stats = JSON.parse(JSON.stringify(editedStats));
		editMode = false;
	}
</script>

<Sectionwrapper id="administrasi" class="pb-0">
	<div class="admin-container">
		<div class="mx-4 flex max-w-4xl flex-col items-start px-2 sm:mx-18 sm:px-6">
			<h2 class="text-left text-2xl font-bold sm:text-3xl">ADMINISTRASI PENDUDUK</h2>
			<h3 class="mb-2 text-left text-base sm:text-xl">
				Beberapa data administrasi penduduk yang berada di Dusun Druju Tegal.<br />
				Data ini diambil dari data kependudukan yang dikelola oleh Pemerintah Desa Plosogede.
			</h3>
			{#if isAdmin}
				{#if !editMode}
					<button
						class="rounded border border-black bg-blue-500 px-4 py-2 text-black hover:bg-blue-600"
						on:click={startEdit}>Edit Data</button
					>
				{:else}
					<div class="flex gap-2">
						<button
							class="rounded border border-black bg-green-500 px-4 py-2 text-black hover:bg-green-600"
							on:click={saveEdit}>Simpan</button
						>
						<button
							class="rounded border border-black bg-gray-400 px-4 py-2 text-black hover:bg-gray-500"
							on:click={cancelEdit}>Batal</button
						>
					</div>
				{/if}
			{/if}
		</div>
		<div class="admin-grid mx-0 sm:mx-22">
			{#if editMode}
				{#each editedStats as stat, i}
					<div class="admin-card">
						<img src={stat.img} alt={stat.label} />
						<input
							type="number"
							class="px-2 py-1 text-center"
							bind:value={editedStats[i].value}
						/>
						<div class="admin-card-label">{stat.label}</div>
					</div>
				{/each}
			{:else}
				{#each stats as stat}
					<div class="admin-card">
						<img src={stat.img} alt={stat.label} />
						<div class="admin-card-value">{stat.value}</div>
						<div class="admin-card-label">{stat.label}</div>
					</div>
				{/each}
			{/if}
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
		text-align: center;
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
