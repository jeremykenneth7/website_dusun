<script>
	import { onMount } from 'svelte';
	import { getDatabase, ref, onValue, push } from 'firebase/database';
	import { initializeApp, getApps } from 'firebase/app';

	const firebaseConfig = {
		apiKey: 'AIzaSyAVI0FRUDLLTxkBRYEuAxFKj9xpfkEm5Ck',
		authDomain: 'websitedusundrujutegal.firebaseapp.com',
		projectId: 'websitedusundrujutegal',
		storageBucket: 'websitedusundrujutegal.appspot.com',
		messagingSenderId: '178102873490',
		appId: '1:178102873490:web:284c1b78586acdbed0654b',
		measurementId: 'G-X1JMSD4XT4',
		databaseURL: 'https://websitedusundrujutegal-default-rtdb.asia-southeast1.firebasedatabase.app/'
	};

	let app;
	if (!getApps().length) {
		app = initializeApp(firebaseConfig);
	} else {
		app = getApps()[0];
	}
	const db = getDatabase(app);

	onMount(() => {
		push(ref(db, 'kunjungan'), {
			waktu: new Date().toISOString(),
			userAgent: navigator.userAgent
		});
	});

	let kunjungan = [];
	let hariIni = 0,
		kemarin = 0,
		mingguIni = 0,
		mingguLalu = 0,
		bulanIni = 0;

	function hitungStatistik() {
		const now = new Date();
		const today = now.toDateString();
		const yesterday = new Date(now);
		yesterday.setDate(now.getDate() - 1);
		const yesterdayStr = yesterday.toDateString();

		const startOfWeek = new Date(now);
		startOfWeek.setDate(now.getDate() - now.getDay());
		const startOfLastWeek = new Date(startOfWeek);
		startOfLastWeek.setDate(startOfWeek.getDate() - 7);

		const startOfMonth = new Date(now.getFullYear(), now.getMonth(), 1);

		hariIni = kunjungan.filter((k) => new Date(k.waktu).toDateString() === today).length;
		kemarin = kunjungan.filter((k) => new Date(k.waktu).toDateString() === yesterdayStr).length;
		mingguIni = kunjungan.filter((k) => new Date(k.waktu) >= startOfWeek).length;
		mingguLalu = kunjungan.filter(
			(k) => new Date(k.waktu) >= startOfLastWeek && new Date(k.waktu) < startOfWeek
		).length;
		bulanIni = kunjungan.filter((k) => new Date(k.waktu) >= startOfMonth).length;
	}

	onMount(() => {
		const kunjunganRef = ref(db, 'kunjungan');
		onValue(kunjunganRef, (snapshot) => {
			const data = snapshot.val();
			kunjungan = data ? Object.values(data) : [];
			hitungStatistik();
		});
	});
</script>

<div class="floating-kunjungan group">
    <b>Statistik Kunjungan</b>
    <ul>
        <li>Hari ini: {hariIni}</li>
        <div class="detail-kunjungan group-hover:block hidden">
            <li>Kemarin: {kemarin}</li>
            <li>Minggu ini: {mingguIni}</li>
            <li>Minggu lalu: {mingguLalu}</li>
            <li>Bulan ini: {bulanIni}</li>
        </div>
    </ul>
</div>

<style>
    .floating-kunjungan {
        position: fixed;
        bottom: 24px;
        right: 24px;
        background: white;
        border-radius: 12px;
        box-shadow: 0 2px 8px rgba(0, 0, 0, 0.15);
        padding: 16px;
        z-index: 1000;
        transition: box-shadow 0.2s;
    }
    .detail-kunjungan {
        margin-top: 8px;
    }
    @media (max-width: 640px) {
        .floating-kunjungan {
            display: none;
        }
    }
</style>