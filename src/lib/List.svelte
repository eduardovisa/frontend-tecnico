<script>
    import FaCheck from 'svelte-icons/fa/FaCheck.svelte';
    import IoIosClose from 'svelte-icons/io/IoIosClose.svelte';

    export let item, updateItem;
</script>

<div class="box-container">
    <div class="grid-container">
        <div style="justify-content: left;" class="grid-item" class:text-disabled={item.status}>
            <h4>{item.titlem}</h4>
        </div>
        <div class="grid-item">
            {#if !item.status}
                <button on:click={() => updateItem(item.id, true)}>
                    <div class="complete-task-icon">
                        <FaCheck />
                    </div>
                </button>
            {:else}
                <button on:click={() => updateItem(item.id, false)}>
                    <div class="delete-task-icon">
                        <IoIosClose />
                    </div>
                </button>
            {/if}
        </div>
        <div class="grid-item">
            <button>
                <div class="delete-task-icon">
                    <IoIosClose />
                </div>
            </button>
        </div>
    </div>
</div>

<style>
    .box-container {
        width: 100%;
        display: flex;
        justify-content: end;
    }
    .grid-container {
        width: 90%;
        display: grid;
        grid-template-columns: 80% 10% 10%;
        background-color: #374151;
        margin-top: 10px;
        border-radius: 10px;
    }
    .grid-item {
        display: flex;
        justify-content: end;
        margin-left: 10px;
        text-align: center;
        box-sizing: border-box;
    }
    .text-disabled {
        color: #6b7280;
        text-decoration: line-through;
    }
    button {
        background-color: transparent;
        box-shadow: none;
        border: none;
        cursor: pointer;
    }
    .complete-task-icon {
        width: 15px;
        color: #28c55b;
    }
    .delete-task-icon {
        width: 30px;
        color: #ef4347;
    }
</style>