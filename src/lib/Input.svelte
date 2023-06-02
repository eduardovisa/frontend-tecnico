<script>
    export let postNewItem, titlem; 
</script>

<div class="box">
    <input placeholder="Add new todo" bind:value={titlem} />
    <button on:click={postNewItem}>Add</button>
</div>

<style>
    .box {
        display: flex;
        flex-direction: row;
    }
    .box input {
        width: 500px;
        border: 2px solid rgb(238, 238, 238);
        box-sizing: border-box;
        padding-left: 10px;
        font-size: large;
    }
    .box button {
        border-radius: 0;
        background-color: #3b82f6;
        border-top-right-radius: 10px;
        border-bottom-right-radius: 10px;
    }
</style>