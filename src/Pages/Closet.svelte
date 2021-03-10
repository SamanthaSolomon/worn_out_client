<script>
//imports
import Header from "../components/Header.svelte"
export let items
export let getOneItem

const handleClick = (id) => {
    window.location.href = `/item/${id}`
}

</script>


<div>
    <Header />
    {#each items as item (item.id)}
    <div>
        <img src={item.img} alt={item.color}{item.style}>
        <h4>{item.style} | {item.color}</h4>
        <p>{item.use} | {item.category}</p>
        <h3>Worn {item.wear_count} times.</h3>
        <button class="details-button" on:click = {() => handleClick(item.id)}>Details ></button>
    </div>
    {:else}
    <h3 class="loading-message">Loading your closet...</h3>
    {/each}
</div>


<style>
    div{
        padding-top: 15%;
        text-align: center;
    }

   img{
       width: 10rem;
   }
   
   h4{
       margin: 10px;
   }

   h3{
       margin: 5px;
   }

   p{
       margin: 5px; 
   }

   .loading-message{
       padding-top: 30%;
   }
</style>