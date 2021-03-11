<script>
//imports
import Header from "../components/Header.svelte"
//libraries
import router from 'page'
//props
export let items
export let getOneItem

const handleClick = (id) => {
    getOneItem(id)
    router(`/item/${id}`)
}

</script>


<div class="closet-div">
    <Header />
    {#each items as item (item.id)}
    <div class="item-div">
        <img src={item.img} alt={item.color}{item.style}>
        <h4>{item.style} | {item.color}</h4>
        <p>{item.use} | {item.category}</p>
        <div class="button-div">
            <button class="details-button" on:click = {() => handleClick(item.id)}>Details  ></button>
        </div>
    </div>
    {:else}
    <h3 class="loading-message">Loading your closet...</h3>
    {/each}
</div>


<style>
    div{
        padding-top: 15%;
        padding-bottom: 15%;
        text-align: center;
    }

   img{
       width: 55%;
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
       text-align: center;
   }

   .button-div{
       padding-top: 30px;
       padding-bottom: 0px;
   }

/* Tablet styles */
 @media only screen and (min-width: 768px){
    div{
        padding-top: 10%;
    }

    h3{
       font-size: 1.5rem;
   }

   img{
       width: 55%;
   }

   .details-button{
       font-size: 1rem;
       padding: 20px;
   }

   .closet-div{
       display: flex;
       flex-flow:row wrap;
       align-items: flex-end;
   }

   .item-div{
       flex-grow: 1;
       flex-basis: 35%;
       padding-bottom: 0;
   }

   .loading-message{
       text-align: center;
   }

}

/* Desktop styles */
@media only screen and (min-width: 1024px){

    .item-div{
       flex-grow: 1;
       flex-basis: 21%;
       padding-bottom: 0.5%;
       padding-top: 1%;
   }

}

</style>