<script>
    let message = '';
    let messages = '';

    function updateMessage(event) {
        console.log(event.target.value);
        message = event.target.value;
    }

    function saveMessage() {
        const newMessage = {
            id: Date.now(),
            text: message,
            author: "Killian",
        };
        messages = [newMessage, ...messages];
        console.log('message :', messages);
    }
</script>
<style>
    * {
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
</style>
<main>
    <h1>Switter</h1>
    <p>Voici ma première app avec Svelte</p>
    <textarea name="" id="" cols="60" rows="5" on:input={updateMessage}></textarea>
    <button on:click={saveMessage}>Envoyer</button>
    <div>
        <h3>Preview</h3>
        {message}
    </div>
    <div>
        <h2>Messages</h2>
        {messages}
    </div>
</main>
