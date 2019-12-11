<script>
    import { createEventDispatcher } from 'svelte';

    const dispatch = createEventDispatcher()
    let note = "";

    const handleChange = (e) => {
        note = e.target.value;
    }

    const handleSubmit = () => {
        dispatch("note", {
            content: note
        })
    }
</script>
<div class="note-section">
    <div class="note-wrapper">
        <h1>"FOR"EVERNOTE</h1>
        <textarea
            name="note"
            placeholder="isi catatan Anda"
            class="note"
            value={note}
            rows="4"
            cols="9"
            on:change={handleChange}
        />
        <button type="submit" class="btn fluid submit" on:click={handleSubmit}>Save</button>
    </div>
</div>
<style>
    h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 3em;
		font-weight: 100;
    }
    
    .note-section {
        display: flex;
        flex-direction: column;
        justify-items: center;
        align-items: center;
        height: 100%;
        background: #FFFFFF;
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