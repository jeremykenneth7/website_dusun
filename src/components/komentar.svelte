<script>
	import Sectionwrapper from './sectionwrapper.svelte';
	import { onMount } from 'svelte';
	import { initializeApp } from 'firebase/app';
	import { getDatabase, ref, push, onValue } from 'firebase/database';

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

	let nama = '';
	let komentar = '';
	let daftarKomentar = [];

	function formatWaktu(dateString) {
		const date = new Date(dateString);
		const bulan = [
			'Januari',
			'Februari',
			'Maret',
			'April',
			'Mei',
			'Juni',
			'Juli',
			'Agustus',
			'September',
			'Oktober',
			'November',
			'Desember'
		];
		const hari = date.getDate();
		const namaBulan = bulan[date.getMonth()];
		const tahun = date.getFullYear();
		const jam = date.getHours().toString().padStart(2, '0');
		const menit = date.getMinutes().toString().padStart(2, '0');
		return `${hari} ${namaBulan} ${tahun} ${jam}.${menit}`;
	}

	function kirimKomentar() {
		if (nama.trim() && komentar.trim()) {
			push(ref(db, 'komentar'), {
				nama,
				komentar,
				waktu: new Date().toISOString()
			});
			nama = '';
			komentar = '';
		}
	}

	onMount(() => {
		const komentarRef = ref(db, 'komentar');
		onValue(komentarRef, (snapshot) => {
			const data = snapshot.val();
			daftarKomentar = data ? Object.values(data).reverse() : [];
		});
	});
</script>

<Sectionwrapper id="komentar" class="pb-0">
	<div class="container mx-0 rounded-2xl bg-gray-50 p-6 shadow-lg sm:mx-22">
		<h2 class="mb-6 text-center text-2xl font-bold">Komentar Pengunjung</h2>
		<form class="mb-8 flex flex-col gap-4" on:submit|preventDefault={kirimKomentar}>
			<input
				type="text"
				placeholder="Nama Anda"
				bind:value={nama}
				required
				class="rounded-lg border border-gray-300 px-4 py-2 focus:ring-2 focus:ring-blue-400 focus:outline-none"
			/>
			<textarea
				rows="3"
				placeholder="Tulis komentar..."
				bind:value={komentar}
				required
				class="resize-none rounded-lg border border-gray-300 px-4 py-2 focus:ring-2 focus:ring-blue-400 focus:outline-none"
			></textarea>
			<button type="submit" class="rounded-lg px-6 py-2 font-semibold text-black transition">
				Kirim Komentar
			</button>
		</form>
		<div class="mx-0 mt-4 sm:mx-22">
			{#if daftarKomentar.length === 0}
				<p class="text-center text-gray-500">Belum ada komentar.</p>
			{:else}
				{#each daftarKomentar as k}
					<div class="mb-4 rounded-lg bg-white p-4 shadow">
						<div class="font-bold text-blue-700">{k.nama}</div>
						<div class="mb-2 text-sm text-gray-500">{formatWaktu(k.waktu)}</div>
						<div>{k.komentar}</div>
					</div>
				{/each}
			{/if}
		</div>
	</div>
</Sectionwrapper>
