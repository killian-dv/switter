<script>
    import Message from "./Message.svelte";
    let messages = "";

    function addMessage(event) {
        console.log(event.detail);
        messages = [event.detail, ...messages];
    }
</script>
<style>
    * {
        padding: 0;
        margin: 0;
        box-sizing: border-box;
        font-family: 'Rubik', sans-serif;
    }
    main {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        height: 100vh;
    }
    h1 {
        color: #1e9cea;
    }
    .chat-message {
        background-color: #1e9cea;
        padding: 0.5rem;
        border-radius: 12px;
        border-bottom-left-radius: 0px;
        color: #fff;
        margin: 0.5rem;
    }
</style>
<main>
    <h1>Switter</h1>
    <p>Voici ma première app avec Svelte</p>
    <Message author="Bob" on:message={addMessage}/>
    <div>
        <h2>Messages</h2>
        {#each messages as message}
            <div class="chat-message">
                <p>By {message.author}</p>
                <p>{message.text}</p>
            </div>
        {/each}
    </div>
</main>
