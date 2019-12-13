<script>
	import Card from "./Card.svelte";
    export let notes;
</script>

<div class="notes">
    {#each notes as note}
        <Card note={note} on:delete on:edit />
    {/each}
</div>

<style>
	.notes {
        display: grid;
        grid-template-columns: auto auto auto auto;
        grid-gap: 10px;
        height: 100%;
	}
</style>