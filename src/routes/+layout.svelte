<script>
	import '../app.css';
	import Contact from '../components/contact.svelte';
	import Footer from '../components/footer.svelte';
	import Header from '../components/header.svelte';

	import { openModal } from '../store';

	let y;
	$: outerHeight = 0;

	function reroute(href) {
		$openModal = false;
		window.location.hash = href;
	}
</script>

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
				on:click={() => reroute('#product')}
				class="group cursor-pointer border-none p-2 text-left duration-200 outline-none"
			>
				<p class="poppins text-3xl font-semibold duration-200 group-hover:pl-2">
					Product<i class="fa-solid fa-chevron-right pl-4 text-xl"></i>
				</p>
			</button>
			<button
				on:click={() => reroute('#review')}
				class="group cursor-pointer border-none p-2 text-left duration-200 outline-none"
			>
				<p class="poppins text-3xl font-semibold duration-200 group-hover:pl-2">
					Review <i class="fa-solid fa-chevron-right pl-4 text-xl"></i>
				</p>
			</button>
			<button
				on:click={() => reroute('#map')}
				class="group cursor-pointer border-none p-2 text-left duration-200 outline-none"
			>
				<p class="poppins text-3xl font-semibold duration-200 group-hover:pl-2">
					Map<i class="fa-solid fa-chevron-right pl-4 text-xl"></i>
				</p>
			</button>
		</div>
		<div class="flex flex-col items-center justify-center">
			<Contact />
		</div>
	</div>
{/if}

{#if y > outerHeight}
    <div
        class="fadeIn fixed top-0 left-0 z-50 flex w-full flex-col bg-gradient-to-br from-slate-900 via-slate-800 to-slate-900 px-4"
    >
        <Header />
    </div>
{/if}
<slot />
<Footer />
<svelte:window bind:scrollY={y} bind:outerHeight />
