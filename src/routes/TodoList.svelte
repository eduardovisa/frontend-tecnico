<script>
    import { onMount } from "svelte";
    
    import supabase from "../lib/client";

    import List from "../lib/List.svelte";
    import Input from "../lib/Input.svelte";

    let itemList = [];

    onMount(async () => {
        getAllItems();
    });

    const getAllItems = async() => {
        try {
            let { data, error } = await supabase.from('todos').select('*');
            itemList = data;
            // console.log(data);
        } catch (error) {
            console.log(error);
        }
    };

    async function postNewItem (titlem) {
        try {
            const { data, error } = await supabase.from('todos').insert([
                { 
                    titlem: titlem, 
                    status: false 
                },
            ]);
            await getAllItems();
        } catch (error) {
            console.log(error);
        }
    };

    async function updateItem (id) {
        try {
            const { data, error } = await supabase.from('todos').update(
                { 
                    status: true 
                }
            ).eq('id', id);
            await getAllItems();
        } catch (error) {
            console.log(error);
        };
    };
</script>

<div class="mainBox">
    <h2>TaskMaster</h2>

    <Input postNewItem={postNewItem} />

    <div>
        {#each itemList as item }
            <List item={item} updateItem={updateItem} />
        {:else}
            <h1>Vacío</h1>
        {/each }
    </div>
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