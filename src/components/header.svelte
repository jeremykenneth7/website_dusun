<script>
	import { openModal } from '../store';
</script>

<header class="relative z-20 flex flex-col">
	<div class="mx-auto flex w-full max-w-[1400px] items-center justify-between p-4 py-6">
		<a href="/" class="flex items-center gap-4">
			<img src="/logo_dusun.png" alt="Logo Dusun Druju Tegal" class="h-12 w-12" />
			<h1 class="font-semibold"><span class="text-white">Dusun Druju Tegal</span></h1>
		</a>
		<button
			on:click={() => ($openModal = true)}
			aria-label="Menu"
			class="grid place-items-center md:hidden"
		>
			<i class="fa-solid fa-bars"></i>
		</button>
		<nav class="hidden items-center gap-4 md:flex lg:gap-6">
			<a
				href="#product"
				class="cursor-pointer font-semibold text-white duration-200 hover:text-indigo-400"
				>Produk</a
			>
			<a
				href="#review"
				class="cursor-pointer font-semibold text-white duration-200 hover:text-indigo-400">Review</a
			>
			<a
				href="#map"
				class="cursor-pointer font-semibold text-white duration-200 hover:text-indigo-400">Peta Dusun</a
			>
		</nav>
	</div>
</header>
