<script>
//imports
import Header from "../components/Header.svelte"
export let items


//see details of one item
const handleClick = (id) => {
    // console.log('this item was clicked-', id)
    window.location.href = `/item/${id}`
}


</script>


<div>
    <Header />
    {#each items as item (item.id)}
    <div on:click = {() => handleClick(item.id)}>
        <img src={item.img} alt={item.color}{item.style}>
        <a href='/item'><h4>{item.style} | {item.color}</h4></a>
        <p>{item.use} | {item.category}</p>
        <h3>Worn {item.wear_count} times since {item.created_at}</h3>
    </div>
    {:else}
    <h3>Loading your closet.</h3>
    {/each}
</div>


<style>
   img {
    width: 10rem
   } 
</style>