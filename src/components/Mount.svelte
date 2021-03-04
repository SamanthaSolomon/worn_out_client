<script>
import {onMount} from "svelte"


let items = []

onMount( async () => {
    const response = await fetch('https://damp-peak-94577.herokuapp.com/users/1/items')
    items = await response.json()

    console.log(items)
})


</script>


<div>
    {#each items as item}
    <p>{item.category}</p>
    {/each}
</div>