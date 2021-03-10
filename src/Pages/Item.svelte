<script>
    //imports
    import Header from '../components/Header.svelte'
    //import item props
    export let item
    //destructure item object
    const { id, img, category, style, use, color, wear_count } = item

    console.log('item-', item)

    let url = 'https://damp-peak-94577.herokuapp.com/users/1/items'

    //Update item wear coun
    // const woreIt = () => {
        
    // }
    
    //Delete item
    const deleteItem = async (id) => {
        const response = await fetch(url + `/${id}`, {
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
        <!-- <button on:click={() => woreIt()}>Wore It!</button>  -->
        <button on:click = {() => deleteItem(item.id)}>Remove item from my closet</button> 
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