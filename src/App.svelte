<script>
	import './normalizr.css';
	import Input from "./Input.svelte";
	import Note from "./Note.svelte";
	let notes = [
		{ id: 'J---aiyznGQ', content: 'Keyboard Cat' },
		{ id: 'z_AbfPXTKms', content: 'Maru' },
		{ id: 'OUtn3pvWmpg', content: 'Henri The Existential Cat' }
	];
	
	const handleCreateNote = e => {
		const note = { id: Math.random(), content: e.detail.content };
		notes = [...notes, note];
	}

	const handleDeleteNote = e => {
		const newNotes = notes.filter(note => note.id !== e.detail.id);
		notes = newNotes;
	}
</script>

<main>
	<div class="left">
		<Input on:note={handleCreateNote} />
	</div>
	<div class="right">
		<Note notes={notes} on:delete={handleDeleteNote} />
	</div>
</main>

<style>
	:global(body) {
		background-color: #f2f2f2;
	}

	main {
		height: 100%;
	}

	.left {
		width: 600px;
		height: 100%;
		position: fixed;
		top: 0;
		left: 0;
		bottom: 0;
	}

	.right {
		margin-left: 600px;
		height: 100%;
	}
</style>