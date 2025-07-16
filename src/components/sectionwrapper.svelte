<script>
    export let id;
</script>

<section {id} class="flex flex-col px-4 my-8 scroll-mt-32">
    <div class="mx-auto flex w-full max-w-[1400px] flex-col">
        <slot />
    </div>
</section>