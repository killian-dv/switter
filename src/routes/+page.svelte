<script>
    import Message from "./Message.svelte";
    let messages = "";

    function addMessage(event) {
        console.log(event.detail);
        messages = [event.detail, ...messages];
    }

    const options = {
        hour: "numeric",
        minute: "2-digit",
        second: "2-digit",
    };

    const formatter = new Intl.DateTimeFormat("fr-FR", options);
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
        gap: 1rem;
        height: 100vh;
    }
    h1 {
        color: #1e9cea;
    }
    h1, h2, h3 {
        text-align: center;
    }
    .chat-message {
        background-color: #1e9cea;
        padding: 0.5rem;
        border-radius: 12px;
        border-bottom-left-radius: 0px;
        color: #fff;
        margin: 0.5rem;
    }
    .chat-message p:first-child {
        font-weight: bold;
    }
</style>
<main>
    <h1>Switter</h1>
    <p>Voici ma première app avec Svelte</p>
    <Message on:message={addMessage}/>
    <div>
        <h2>Messages</h2>
        {#each messages as message}
            <div class="chat-message">
                <p>De {message.author} à {formatter.format(message.date)}</p>
                <p>{message.text}</p>
            </div>
        {/each}
    </div>
</main>
