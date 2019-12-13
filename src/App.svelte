<script>
	import './normalizr.css';
	import Input from "./Input.svelte";
	import Note from "./Note.svelte";
	import Modal from "./Modal.svelte";
	let showModal = false;
	let selectedNote = { id: "", content: ""};
	let notes = [
		{ id: 'J---aiyznGQ', content: 'Keyboard Cat' },
		{ id: 'z_AbfPXTKms', content: 'Maru' },
		{ id: 'OUtn3pvWmpg', content: 'Henri The Existential Cat' },
		{ id: 'OUtn3pvWmpg', content: 'Henri The Existential Cat' }
	];
	
	const handleCreateNote = e => {
		const note = { id: Math.random(), content: e.detail.content };
		notes = [...notes, note];
	}

	const handleEditNote = e => {
		const note = notes.find(note => note.id === selectedNote.id);
	}

	const handleDeleteNote = e => {
		const newNotes = notes.filter(note => note.id !== e.detail.id);
		notes = newNotes;
	}

	const openModal = () => {
		showModal = true
	}

	const closeModal = () => {
		showModal = false
	}

	const handleEdit = e => {
		selectedNote = e.detail.note;
		openModal();
	}
</script>

<main>
	<div class="header">
		<h3 class="logo">FOREVER NOTE</h3>
	</div>
	<div class="main-content">
		<div>
			<button class="btn" on:click={openModal}>+ Add New</button>
		</div>
		<Note notes={notes} on:delete={handleDeleteNote} on:edit={handleEdit} />
		{#if showModal}
			<Modal on:close={closeModal} >
				<Input on:note={handleCreateNote} note={selectedNote} />
			</Modal>
		{/if}
	</div>
</main>

<style>
	:global(body) {
		background-color: #f2f2f2;
		padding: 0;
	}

	.header {
		background-color: #f3e36d;;
		padding: 0.5em 1em;
		box-shadow: 0 1px 3px rgba(0,0,0,0.16), 0 1px 3px rgba(0,0,0,0.23);
	}

	.logo {
		color: rgb(216, 15, 99);
	}

	main {
		height: 100%;
	}

	.main-content {
		padding: 1em;
	}
</style>