<script>
    import Contact from './contact.svelte';
    import Header from './header.svelte';
    import Sectionwrapper from './sectionwrapper.svelte';
    import { onMount } from 'svelte';

    const parts = [
        { text: 'Selamat Datang', class: 'text-indigo-400' },
        { text: ' di Website', class: 'text-white' },
        { text: ' Dusun Druju Tegal', class: 'text-gray-200' }
    ];

    let displayed = ['', '', ''];

    onMount(() => {
        let partIdx = 0;
        let charIdx = 0;

        function typeNextChar() {
            if (partIdx < parts.length) {
                if (charIdx < parts[partIdx].text.length) {
                    displayed[partIdx] += parts[partIdx].text[charIdx];
                    charIdx++;
                    setTimeout(typeNextChar, 70);
                } else {
                    partIdx++;
                    charIdx = 0;
                    setTimeout(typeNextChar, 300);
                }
            }
        }
        typeNextChar();
    });
</script>

<div
    class="relative min-h-screen bg-cover bg-center bg-no-repeat"
    style="background-image: url('/wallpaper/dusun.jpeg');"
>
    <!-- Overlay untuk readability -->
    <div class="absolute inset-0 bg-black/40"></div>

    <!-- Content -->
    <div class="relative z-10">
        <Sectionwrapper>
            <Header />
            <div
                class="flex min-h-[80vh] flex-1 flex-col items-center justify-center gap-10 pb-10 md:pb-14"
            >
            <h2 class="mx-auto w-full max-w-[1200px] text-center text-4xl font-semibold text-white sm:text-5xl md:text-6xl lg:text-7xl">
                {#each parts as part, i}
                    <span class={part.class}>{displayed[i]}</span>
                {/each}
                <span class="text-white animate-blink">|</span>
            </h2>
                <p
                    class="mx-auto w-full max-w-[1000px] text-center text-xl text-gray-100 sm:text-2xl md:text-3xl lg:text-4xl"
                >
                    Website ini dibuat untuk memudahkan warga Dusun Druju Tegal dalam mengakses informasi dan
                    layanan yang tersedia.
                </p>

                <Contact />
            </div>
        </Sectionwrapper>
    </div>
</div>

<style>
    .animate-blink {
        animation: blink 1s steps(1) infinite;
        margin-left: 2px;
    }
    @keyframes blink {
        0%, 50% { opacity: 1; }
        51%, 100% { opacity: 0; }
    }
</style>