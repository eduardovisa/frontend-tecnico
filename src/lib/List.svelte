<script>
    export let item;
</script>

<div class="main-box">
    <div class="grid-container">
        <div style="justify-content: left;" class="grid-item">
            <h4>{item.titlem}</h4>
        </div>
        <div class="grid-item">
            <input type="checkbox" checked={item.status} />
        </div>
        <div class="grid-item">
            <button>Eliminar</button>
        </div>
    </div>
</div>

<style>
    .main-box {
        width: 100%;
        display: flex;
        justify-content: end;
    }
    .grid-container {
        width: 80%;
        display: grid;
        grid-template-columns: 70% auto auto;
        background-color: #374151;
        border-radius: 10px;
        margin-top: 10px;
    }
    .grid-item {
        display: flex;
        text-align: center;
        justify-content: end;
        margin-left: 10px;
    }
</style>