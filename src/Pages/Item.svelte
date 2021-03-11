<script>
    //imports
    import Header from '../components/Header.svelte'
    //libraries
    import router from 'page'
    import { createEventDispatcher } from 'svelte'
    //import item props
    export let item
    //variables
    const dispatch = createEventDispatcher()
    let url = 'https://damp-peak-94577.herokuapp.com/users/1/items'

    //Dispatch woreIt handleClick to app
    const woreIt = (wear_count, id) => {
        dispatch('addCount', {wear_count: wear_count, id: id})
    }
    
    // Delete item
    const deleteItem = async (item) => {
        // console.log('item-', item)
        const response = await fetch(url + `/${item.id}`, {
            method: "DELETE",
            headers: {
                "Content-Type": "application/json"
            },
        })
        if(response.ok){
            router(`/closet`)
        }
    }
</script>



<div class="item-page">
    <div class="item-div">
        <Header />
        <div class="img-style-color">
            <img src={item.img} alt={item.color}{item.style}>
            <h4>{item.style} | {item.color}</h4>
            <p>{item.use} | {item.category}</p>
        </div>
        <div class="wear-count-buttons">    
            <h3>Worn {item.wear_count} times.</h3>
            <div class="button-div">
                <button on:click={() => woreIt(item.wear_count, item.id)}>Wore It!</button> 
            </div>
            <div class="button-div">
                <button on:click = {() => deleteItem(item)}>Toss It!</button>
            </div> 
        </div>
    </div> 
</div>

<style>
     div{
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

   .button-div{
      padding-top: 20px;
      padding-bottom: 20px; 
   }

/* Tablet styles */
@media only screen and (min-width: 768px){

    .item-div{
        padding-top: 15%;
        padding-bottom: 15%;
        display: grid;
        grid-template-columns: 1fr 1fr;
        grid-template-rows: 1fr;
    }

    .img-style-color{
        display: flex;
        flex-direction: column;
        justify-content: flex-start;
        grid-column-start: 1;
        grid-column-end: 2;
        justify-self: end;
        align-self: end;
    }

    .wear-count-buttons{
        display: flex;
        flex-direction: column;
        grid-column-start: 2;
        grid-column-end: 3;
        justify-self: center;
        align-self: center;
    }

    button{
        padding: 7%;
    }

    img{
        width: 20rem;
    
    }

    h3{
        font-size: 2rem;
    }

}

@media only screen and (min-width: 1024px){
    button{
        padding: 9%;
    }

    img{
        width: 25rem;
    }

    h4{
        font-size: 2rem;
    }

    p{
        font-size: 1.5rem;
    }
}
</style>