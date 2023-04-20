<script>
    import { createEventDispatcher } from "svelte";
    const dispatch = createEventDispatcher();
    let message = "";
    let author = "";
    let maxlength = 24;
    $: nbCaracters = message.length;
    $: disabled = message.length === 0 || message.length > maxlength  ? true : false;

    function saveMessage() {
        const newMessage = {
            id: Date.now(),
            text: message,
            author: author || "Anonyme",
            date: new Date(),
        };
        // messages = [newMessage, ...messages];
        dispatch("message", newMessage);
        message = "";
        author = "";
    }
</script>
<style>
    .container {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
    }
    .text-input {
        width: 100%;
        padding: 0.5rem;
        border: 1px solid #ccc;
        border-radius: 4px;
        margin-bottom: 0.5rem;
    }
    textarea {
        width: 100%;
        padding: 0.5rem;
        border: 1px solid #ccc;
        border-radius: 4px;
        margin-bottom: 0.5rem;
    }
    button {
        all: unset;
        padding: 0.5rem 1rem;
        border-radius: 4px;
        background-color: #1e9cea;
        color: #fff;
        cursor: pointer;
    }
    button:disabled {
        background-color: #ccc;
        cursor: not-allowed;
    }
    .alert {
        color: orangered;
    }
</style>
<div class="container">
    <input class="text-input" type="text" bind:value={author}>
    <textarea name="" id="" cols="60" rows="5" bind:value={message}></textarea>
    <div>
        <button on:click={saveMessage} disabled={disabled}>Envoyer</button>
        <span class:alert={nbCaracters > maxlength}>{nbCaracters}</span>
        {#if message.length > maxlength}
            <span class="alert">Le message est trop long</span>
        {/if}
    </div>
</div>
