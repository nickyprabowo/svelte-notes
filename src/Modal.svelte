<script>
    export let header = "Create Note";
    import { createEventDispatcher } from 'svelte';

    const dispatch = createEventDispatcher()
    const handleClose = () => {
        dispatch("close")
    };
</script>
<div class="modal-overlay">
    <div class="modal">
        <div class="modal-header">
            <h2>{header}</h2>
            <span class="close-modal" on:click={handleClose}>X</span>
        </div>
        <div class="modal-body">
            <slot></slot>
        </div>
        <div class="modal-footer"></div>
    </div>
</div>
<style>
    .modal-overlay {
        background-color: rgba(0, 0, 0, 0.288);
        display: flex;
        align-content: center;
        justify-content: center;
        position: absolute;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
    }

    .modal {
        background-color: #FFFFFF;
        margin: 10% auto;
        width: 50%;
    }

    .modal-header {
        padding: 0.2em 1em;
        background-color: #f6ffba;
        display: flex;
        justify-content: space-between;
        align-items: center;
    }

    .close-modal {
        cursor: pointer;
    }
</style>