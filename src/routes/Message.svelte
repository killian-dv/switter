<script>
    import { createEventDispatcher } from "svelte";
    const dispatch = createEventDispatcher();
    let message = "";
    export let author;

    function saveMessage() {
        const newMessage = {
            id: Date.now(),
            text: message,
            author: author,
        };
        // messages = [newMessage, ...messages];
        dispatch("message", newMessage);
        message = ""
    }
</script>
<style>

</style>

<textarea name="" id="" cols="60" rows="5" bind:value={message}></textarea>
<button on:click={saveMessage}>Envoyer</button>