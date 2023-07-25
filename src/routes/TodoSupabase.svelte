<script>
    import { onMount } from "svelte";
    
    import supabase from "../component/client";

    import List from "../component/List.svelte";
    import Input from "../component/Input.svelte";

    let itemList = [];
    let itemListCompleted = 0;

    onMount(async () => {
        getAllItems();
    });

    const getAllItems = async() => {
        try {
            let { data, error } = await supabase.from('todos').select('*').order('id', { ascending: true });
            itemList = data;
            itemListCompleted = itemList.filter(item => item.status == true).length;
            // console.log(data);
        } catch (error) {
            console.log(error);
        };
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
        };
    };

    async function updateItem (id, status) {
        try {
            const { data, error } = await supabase.from('todos').update(
                { 
                    status: status
                }
            ).eq('id', id);
            await getAllItems();
        } catch (error) {
            console.log(error);
        };
    };

    async function deleteItem (id) {
        try {   
            const { data, error } = await supabase.from('todos').delete().eq('id', id);
            await getAllItems();
        } catch (error) {
            console.log(error);
        };
    };
</script>

<div class="box-container">
    <h2>Todo-List</h2>

    <Input postNewItem={postNewItem} />

    {#each itemList as item }
        <List item={item} updateItem={updateItem} deleteItem={deleteItem} />
    {:else}
        <h1>Empty</h1>
    {/each }

    <div style="text-align: left;">
        <p>Todal Todos: {itemList.length} | Completed Todos: {itemListCompleted}</p>
        <p style="font-weight: bold;"><i>"The future belongs to those who believe in the beauty of their 
            <br /> dreams."</i> - Eleanor Roosevelt</p>
    </div>
</div>

<style>
    .box-container {
        display: flex;
        flex-direction: column;
        background-color: #1f2937;
        padding: 2rem;
        border-radius: 10px;
    }
    .box-container h2 {
        text-align: left;
    }
</style>