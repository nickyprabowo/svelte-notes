<script>
    import { createEventDispatcher } from 'svelte';

    const dispatch = createEventDispatcher()
    export let note = { id: "", content: "" };
    export let onEdit = false;

    const handleChange = (e) => {
        if (onEdit) {
            note = { id: note.id, content: e.target.value };
        }
        note = e.target.value;
    }

    const handleSubmit = () => {
        dispatch("note", {
            content: note
        })
        note = { id: "", content: "" };
    }
</script>
<div class="note-section">
    <div class="note-wrapper">
        <textarea
            name="note"
            placeholder="isi catatan Anda"
            class="note"
            bind:value={note.content}
            rows="6"
            cols="9"
            on:change={handleChange}
        />
        <button type="submit" class="btn fluid submit" on:click={handleSubmit}>Save</button>
    </div>
</div>
<style>    
    .note-section {
        display: flex;
        flex-direction: column;
        justify-items: center;
        align-items: center;
        height: 100%;
        background: #FFFFFF;
    }

    .note-wrapper {
        width: 80%;
    }

	.note {
		width: 100%;
		margin: 1em 0;
	}

	.btn {
		padding: 0.5em 1em;
	}

	.fluid {
		width: 100%;
	}

	.submit {
		background-color: rgb(63, 101, 228);
		color: white;
		cursor: pointer;
	}

	.submit:hover, .submit:active {
		background-color: rgb(14, 72, 199);
	}
</style>