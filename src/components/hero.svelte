<script>
    import Contact from './contact.svelte';
    import Header from './header.svelte';
    import Sectionwrapper from './sectionwrapper.svelte';
</script>

<div
    class="relative min-h-screen bg-cover bg-center bg-no-repeat"
    style="background-image: url('/desa.jpg');"
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
                <h2
                    class="mx-auto w-full max-w-[1200px] text-center text-4xl font-semibold text-white sm:text-5xl md:text-6xl lg:text-7xl"
                >
                    <span class="text-indigo-400">Selamat Datang</span> di Website
                    <span class="text-gray-200">Dusun Druju Tegal</span>
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