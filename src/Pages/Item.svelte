<script>
    //imports
    import Header from '../components/Header.svelte'
    

    //Delete item
    const handleClick = () => {
        console.log('delete button clicked')
    }

</script>



<div class="item">
    <Header />
    <img src={item.img} alt={item.color}{item.style}>
    <h4>{item.style} | {item.color}</h4>
    <p>{item.use} | {item.category}</p>
    <h3>Worn {item.wear_count} times since {item.created_at}</h3>
    <button on:click={() => handleClick()}>Remove item from my closet</button>  
</div>

<style>
    img {
     width: 10rem
    } 
 </style>