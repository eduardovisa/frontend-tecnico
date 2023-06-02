<script>
    import { onMount } from "svelte";
    
    import supabase from "../lib/client";

    import List from "../lib/List.svelte";
    import Input from "../lib/Input.svelte";

    let titlem = '';
    let itemList = [];

    onMount(async () => {
        getAllItems();
    });

    const getAllItems = async() => {
        let { data, error } = await supabase.from('todos').select('*');
        itemList = data;
    };

    async function postNewItem () {
        const { data, error } = await supabase.from('todos').insert([
            { 
                titlem: titlem, 
                status: false 
            },
        ]);
        await getAllItems();
    };
</script>

<div class="mainBox">
    <h2>TaskMaster</h2>

    <Input postNewItem={postNewItem} titlem={titlem} />

    {#each itemList as item }
        <List item={item} />
    {:else}
        <h1>Vacío</h1>
    {/each }
</div>

<style>
    .mainBox {
        display: flex;
        flex-direction: column;
        background-color: #1f2937;
        padding: 2rem;
        border-radius: 10px;
    }
    .mainBox h2 {
        text-align: left;
    }
</style>