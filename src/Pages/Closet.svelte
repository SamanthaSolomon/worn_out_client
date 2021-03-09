<script>
//libraries
import { onMount } from "svelte"

//imports
import Header from "../components/Header.svelte"

//api call for all items
// let items = []

// onMount( async () => {
//     const response = await fetch('https://damp-peak-94577.herokuapp.com/users/1/items')
//     items = await response.json()

// })


</script>


<div>
    <Header />
    {#each items as item (item.id)}
    <img src={item.img} alt={item.color}{item.style}>
    <a href='/item'><h4>{item.style} | {item.color}</h4></a>
    <p>{item.use} | {item.category}</p>
    <h3>Worn {item.wear_count} times since {item.created_at}</h3>
    {:else}
    <h3>There are no items in your closet.</h3>
    {/each}
</div>

<style>
   img {
    width: 10rem
   } 
</style>