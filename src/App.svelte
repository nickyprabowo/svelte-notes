<script>
	import './normalizr.css';
	import Input from "./Input.svelte";
	import Note from "./Note.svelte";
	import Modal from "./Modal.svelte";
	let showModal = false;
	let onEdit = false;
	let selectedNote = { id: "", content: ""};
	let notes = [
		{ id: 'J---aiyznGQ', content: 'Keyboard Cat' },
		{ id: 'z_AbfPXTKms', content: 'Maru' },
		{ id: 'OUtn3pvWmpg', content: 'Henri The Existential Cat' },
		{ id: 'Utn3pvmpg', content: 'Asereje' }
	];
	
	const handleCreateNote = e => {
		if (onEdit) {
			notes = notes.map(note => {
				if (note.id === selectedNote.id) {
					return {
						...note,
						content: e.detail.content
					}
				}
				return note
			});
			closeEdit();
		} else {
			const note = { id: Math.random(), content: e.detail.content };
			notes = [...notes, note];
			closeModal();
		}
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
		onEdit = true;
		openModal();
	}

	const closeEdit = e => {
		selectedNote = { id: "", content: ""};
		onEdit = false;
		closeModal();
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
			<Modal on:close={closeEdit} >
				<Input on:note={handleCreateNote} note={selectedNote} onEdit={onEdit} />
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