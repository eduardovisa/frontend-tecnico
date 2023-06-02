<script>
    export let item;
</script>

<div class="box">
    <h2>{item.titlem}</h2>
    <input type="checkbox" />
    <button>Eliminar</button>
</div>

<style>
    .box {
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: end;
        gap: 10px;
    }
</style>