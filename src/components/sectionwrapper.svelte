<script>
    export let id;
</script>

<section {id} class="my-8 flex w-full flex-col px-4 scroll-mt-32 sm:px-6 lg:px-8">
    <div class="flex w-full flex-col">
        <slot />
    </div>
</section>