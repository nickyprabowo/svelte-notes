<script>
	import Card from "./Card.svelte";
    export let notes;
</script>

<div class="notes">
    {#each notes as note}
        <Card note={note} on:delete />
    {/each}
</div>

<style>
	.notes {
		display: flex;
        flex-direction: column;
        justify-items: center;
        align-items: center;
        height: 100%;
	}
</style>