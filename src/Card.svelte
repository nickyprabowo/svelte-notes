<script>
    import { createEventDispatcher } from 'svelte';

    const dispatch = createEventDispatcher()
    export let note = {};

    let onEdit = false;
    const handleDelete = () => {
        dispatch("delete", {
            id: note.id
        })
    };

    const handleEdit = () => {
        dispatch("edit", {
            note
        })
    }
</script>

<div class="card">
    <p>{note.content}</p>
    <button on:click={handleDelete}>Delete</button>
    <button on:click={handleEdit}>Edit</button>
</div>

<style>
    .card {
        background: #FFFFFF;
        padding: 1em;
        box-shadow: 0 3px 6px rgba(0,0,0,0.16), 0 3px 6px rgba(0,0,0,0.23);
        margin: 0.5em 0;
        color: black;
    }
</style>