<script>
    import Message from "./Message.svelte";
    let messages = "";
    let isVisible = true;

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

    function toggle () {
        isVisible = !isVisible;
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
    .show {
        all: unset;
        padding: 0.5rem 1rem;
        border-radius: 4px;
        border: solid 2px #1e9cea;
        color: #1e9cea;
        cursor: pointer;
    }
</style>
<main>
    <h1>Switter</h1>
    <p>Voici ma première app avec Svelte</p>
    <button class="show" on:click={toggle}>{isVisible ? "Masquer le formulaire" : "Afficher le formulaire"}</button>
    {#if isVisible}
        <Message on:message={addMessage}/>
    {/if}
    
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
