<script>
	import { goto } from '$app/navigation';
	let username = '';
	let password = '';
	let errorMessage = '';

	function handleSubmit() {
		if (username === 'admin' && password === 'slondok123') {
			alert('Login Berhasil!');
			localStorage.setItem('isAdmin', 'true');
			goto('/');
		} else {
			errorMessage = 'Username atau password salah. Silakan coba lagi.';
		}
	}
</script>

<main
	class="flex min-h-screen flex-col items-center justify-center bg-gray-100"
	style="background-image: url('/wallpaper/dusun.jpeg'); background-size: cover; background-position: center;"
>
	<h1 class="mb-6 text-3xl font-semibold text-white">Admin Login</h1>
	<form on:submit|preventDefault={handleSubmit} class="w-80 rounded bg-white p-6 shadow-md">
		<div class="mb-4">
			<label for="username" class="block text-sm font-medium text-gray-700">Username</label>
			<input
				type="text"
				id="username"
				bind:value={username}
				class="mt-1 block w-full rounded border border-gray-300 p-2"
				required
			/>
		</div>
		<div class="mb-4">
			<label for="password" class="block text-sm font-medium text-gray-700">Password</label>
			<input
				type="password"
				id="password"
				bind:value={password}
				class="mt-1 block w-full rounded border border-gray-300 p-2"
				required
			/>
		</div>
		{#if errorMessage}
			<p class="mb-4 text-sm text-red-500">{errorMessage}</p>
		{/if}
		<button type="submit" class="block w-full rounded border border-gray-300 p-2">Login</button>
	</form>
</main>
