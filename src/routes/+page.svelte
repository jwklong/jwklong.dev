<script>
    import Icon from "$lib/components/icon/icon.svelte";


</script>

<div class="root">
    <Icon size="256px" />
    <div class="info">
        <h1>jwklong</h1>
    </div>
</div>

<style>
    .root {
        display: flex;
        align-items: center;
        justify-content: center;
        width: 100%;
        height: 100%;
        font-size: 2rem;
        font-weight: bold;
        gap: 64px;
    }

    .info {
        display: flex;
        height: 256px;
        align-items: flex-start;
        justify-content: flex-start;
    }

    .info h1 {
        margin: 0;
    }
</style>