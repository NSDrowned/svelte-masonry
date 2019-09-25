<script>
    import { onMount } from 'svelte';
    export let items;
    export let component;
    export let maxcolumns;
    export let gutterwidth;

    let screenWidth;
    let columnwidth;

    function setColumnWidth(maxcolumns, screenWidth) {
        columnwidth = Math.floor((screenWidth) / maxcolumns);
    }

    onMount(() => {
        screenWidth  = (window.innerWidth || document.documentElement.clientWidth || document.body.clientWidth);
        setColumnWidth(maxcolumns, screenWidth);
    });

</script>

<style>
    .grid {
        width: 100%;
        height: 100%;
        display: grid;
        row-gap: 8px;
        grid-auto-rows: 0;
        position: absolute;
        left: 0;
        padding: 14px;
        box-sizing: border-box;
    }
    :global(.item) {
        min-height: 50px;
        background-color: #CCC;
        padding: 14px;
        border-radius: 4px;
        text-align: center;
        box-sizing: border-box;
        border: 1px solid #F00;
    }
</style>

<div id="grid" class="grid" style="grid-template-columns: repeat(auto-fill, minmax({columnwidth}px, 1fr))">
    {#each items as item, i}
    <svelte:component this={component} width={columnwidth} {...item} />
    {/each}
</div>