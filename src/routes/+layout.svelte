<script>
	import '../app.css';
	import Contact from '../components/contact.svelte';
	import Footer from '../components/footer.svelte';
	import Header from '../components/header.svelte';

	import { openModal } from '../store';
	import { goto } from '$app/navigation';

	let y;
	$: outerHeight = 0;

	function reroute(href) {
		$openModal = false;
		window.location.hash = href;
	}

	let isAdmin = false;
	if (typeof window !== 'undefined') {
		isAdmin = localStorage.getItem('isAdmin') === 'true';
	}

	function logout() {
		if (typeof window !== 'undefined') {
			localStorage.removeItem('isAdmin');
			location.reload();
		}
	}
</script>

<svelte:head>
	<title>Dusun Druju Tegal Plosogede - Profil, Potensi, Dokumentasi</title>
	<meta property="og:title" content="Dusun Druju Tegal Plosogede" />
	<meta property="og:description" content="Informasi lengkap Dusun Druju Tegal Plosogede." />
	<meta property="og:url" content="https://drujutegal.com" />
	<meta
		name="description"
		content="Website resmi Dusun Druju Tegal Plosogede. Informasi administrasi, potensi, dokumentasi, dan struktur dusun."
	/>
	<meta
		name="keywords"
		content="dusun drujutegal, drujutegal, dusun drujutegal plosogede, desa plosogede, profil dusun, administrasi dusun"
	/>
</svelte:head>

{#if $openModal}
	<div
		class="fixed top-0 left-0 z-50 flex h-screen w-screen flex-col gap-8 border-b bg-white p-5 px-8 md:hidden"
	>
		<div class="flex items-center justify-between gap-4 border-b pb-2">
			<h1 class="font-semibold">
				Dusun <span class="text-indigo-400">Druju Tegal</span>
			</h1>
			<button
				on:click={() => ($openModal = false)}
				class="border-none outline-none"
				aria-label="Close Modal"
			>
				<i class="fa-solid fa-xmark text-2xl"></i>
			</button>
		</div>
		<div class="flex flex-1 flex-col gap-4">
			<button
				on:click={() => reroute('#map')}
				class="group cursor-pointer border-none p-2 text-left duration-200 outline-none"
			>
				<p class="poppins text-2xl font-semibold duration-200 group-hover:pl-2">
					Peta Administrasi<i class="fa-solid fa-chevron-right pl-4 text-xl"></i>
				</p>
			</button>
			<button
				on:click={() => reroute('#struktur_dusun')}
				class="group cursor-pointer border-none p-2 text-left duration-200 outline-none"
			>
				<p class="poppins text-2xl font-semibold duration-200 group-hover:pl-2">
					Struktur Dusun <i class="fa-solid fa-chevron-right pl-4 text-xl"></i>
				</p>
			</button>
			<button
				on:click={() => reroute('#potensi')}
				class="group cursor-pointer border-none p-2 text-left duration-200 outline-none"
			>
				<p class="poppins text-2xl font-semibold duration-200 group-hover:pl-2">
					Potensi <i class="fa-solid fa-chevron-right pl-4 text-xl"></i>
				</p>
			</button>
			<button
				on:click={() => reroute('#dokumentasi')}
				class="group cursor-pointer border-none p-2 text-left duration-200 outline-none"
			>
				<p class="poppins text-2xl font-semibold duration-200 group-hover:pl-2">
					Dokumentasi<i class="fa-solid fa-chevron-right pl-4 text-xl"></i>
				</p>
			</button>
			<button
				on:click={() => {
					$openModal = false;
					if (isAdmin) {
						logout();
					} else {
						goto('/admin');
					}
				}}
				class="group cursor-pointer border-none p-2 text-left duration-200 outline-none"
			>
				<p class="poppins text-2xl font-semibold duration-200 group-hover:pl-2">
					{#if isAdmin}
						Logout <i class="fa-solid fa-chevron-right pl-4 text-xl"></i>
					{:else}
						Halaman Admin <i class="fa-solid fa-chevron-right pl-4 text-xl"></i>
					{/if}
				</p>
			</button>
		</div>
	</div>
{/if}

{#if y > outerHeight && !$openModal}
	<div
		class="fadeIn fixed top-0 left-0 z-50 flex w-full flex-col bg-gradient-to-br from-slate-900 via-slate-800 to-slate-900 px-4"
	>
		<Header />
	</div>
{/if}
<slot />
<Footer />
<svelte:window bind:scrollY={y} bind:outerHeight />
