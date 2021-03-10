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
    
    // async (wear_count, item) => {

    //     const response = await fetch (url + `/${item.id}`, {
    //         method: "PUT",
    //         headers: {
    //             "Content-Type": "application/json"
    //         },
    //         body: JSON.stringify(item)
    //     })
    //     if(response.ok){
    //         const result = await response.json()
    //     }
    // }
    
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



<div class="item">
    <Header />
    <div>
        <img src={item.img} alt={item.color}{item.style}>
        <h4>{item.style} | {item.color}</h4>
        <p>{item.use} | {item.category}</p>
        <h3>Worn {item.wear_count} times.</h3>
        <button on:click={() => woreIt(item.wear_count, item.id)}>Wore It!</button> 
        <button on:click = {() => deleteItem(item)}>Remove item from my closet</button> 
    </div> 
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
</style>