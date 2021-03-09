<script>
export let message
let successMessage = true
export let isAdded = false
</script>

{#if successMessage}
    <div class="backdrop" class:added={isAdded}>
        <div class ="modal">
            <p>{message}</p>
        </div>
    </div>
{/if}

<style>
    .backdrop{
        width: 100%;
        height: 100%;
        position: fixed;
        background: rgba(27, 56, 64, 0.8)
    }

    .modal{
        padding: 10px;
        max-width: 400px;
        margin: 10px auto;
        text-align: center;
        background: white
    }
</style>