<script>
    export let postNewItem; 

    let titlem = '';
</script>

<div class="box-container">
    <input placeholder="Add new todo" bind:value={titlem} />
    <button disabled={titlem.length==0} on:click={
        () => {
            postNewItem(titlem);
            titlem = '';
        }} 
    >Add</button>
</div>

<style>
    .box-container {
        display: flex;
        flex-direction: row;
    }
    .box-container input {
        width: 500px;
        border: 2px solid #9ca3af;
        box-sizing: border-box;
        padding-left: 10px;
        padding-right: 10px;
        font-size: large;
        border-top-left-radius: 10px;
        border-bottom-left-radius: 10px;
    }
    .box-container button {
        border-radius: 0;
        background-color: #3b82f6;
        border-top-right-radius: 10px;
        border-bottom-right-radius: 10px;
        border: 1px solid transparent;
        padding: 0.6em 1.2em;
        font-size: 1em;
        font-weight: 500;
        font-family: inherit;
        cursor: pointer;
        transition: border-color 0.25s;
    }
    button:hover {
        background-color: #286fb1;
    }
    button:disabled {
        color: white;
    }
</style>