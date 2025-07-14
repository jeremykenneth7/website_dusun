<script>
	import { openModal } from '../store';
</script>

<header class="relative z-20 flex flex-col">
	<div class="mx-auto flex w-full max-w-[1400px] items-center justify-between px-4 py-2">
		<a href="/" class="flex items-center gap-4">
			<img src="/logo_dusun.png" alt="Logo Dusun Druju Tegal" class="h-20 w-20" />
			<div class="flex flex-col">
				<h1 class="font-semibold">
					<span class="text-white">Dusun Druju Tegal</span>
				</h1>
				<h1 class="font-xs">
					<span class="text-white">Plosogede, Kec. Ngluwar, Kabupaten Magelang, Jawa Tengah</span>
				</h1>
			</div>
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
				class="cursor-pointer font-semibold text-white duration-200 hover:text-indigo-400">Produk</a
			>
			<a
				href="#review"
				class="cursor-pointer font-semibold text-white duration-200 hover:text-indigo-400">Review</a
			>
			<a
				href="#map"
				class="cursor-pointer font-semibold text-white duration-200 hover:text-indigo-400"
				>Peta Dusun</a
			>
		</nav>
	</div>
</header>
