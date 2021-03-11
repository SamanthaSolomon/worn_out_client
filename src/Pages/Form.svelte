<script>
    //imports
    import Header from '../components/Header.svelte'
    import Modal from '../components/Modal.svelte'
    
    //show modal
    let successMessage = false

    const toggleModal = () => {
        successMessage = !successMessage
    }

    //Post new item
    let url = 'https://damp-peak-94577.herokuapp.com/users/1/items'
    let img = null, 
        category = null, 
        style = null, 
        color = null, 
        use = null

    async function handleSubmit(){
        const post = { img, category, style, color, use }
        const response = await fetch(url, {
            method: "POST",
            headers: {
                "Content-Type": "application/json"
            },
            body: JSON.stringify(post)
        })
        if(response.ok){
            const result = await response.json()
            toggleModal()  
        }
    }
 </script>




<Header />
<Modal 
    message="New item added to closet!" 
    isAdded={true} 
    successMessage={successMessage}
    on:click={toggleModal}/>
<div class="form">
    <p>Add new item to my closet</p>
    <form class="form-inputs" on:submit={handleSubmit}>
        <label for="img">Image (url)</label>
        <input id="img" 
        name="img"
        bind:value={img}
        />

        <label for="category">Category</label>
        <select
        id="category"
        name="category"
        bind:value={category}>
        <option></option>
        <option>Top</option>
        <option>Bottom</option>
        <option>Shoes</option>
        <option>Onepeice</option>
        <option>Accessory</option>
        <option>Outerwear</option>
        </select>

        <label for="style">Style</label>
        <select
        id="style"
        name="style"
        bind:value={style}>
        <option></option>
        <option>Sweater</option>
        <option>Sweatshirt</option>
        <option>T-shirt</option>
        <option>Tank-top</option>
        <option>Button-up</option>
        <option>Long-sleaved</option>
        <option>Pants</option>
        <option>Leggings</option>
        <option>Sweatpants</option>
        <option>Shorts</option>
        <option>Skirt</option>
        <option>Dress</option>
        <option>Jumpsuit</option>
        <option>Overcoat</option>
        <option>Jacket</option>
        <option>Sneaker</option>
        <option>Bag</option>
        <option>Heels</option>
        <option>Boots</option>
        </select>

        <label for="use">Use</label>
        <select
        id="use"
        name="use"
        bind:value={use}>
        <option></option>
        <option>Everday</option>
        <option>Work</option>
        <option>Specialty</option>
        <option>Workout</option>
        <option>Outdoor</option>
        <option>Sleep/lounge</option>
        </select>

        <label for="style">Color</label>
        <select
        id="color"
        name="color"
        bind:value={color}>
        <option></option>
        <option>Blue</option>
        <option>Black</option>
        <option>Grey</option>
        <option>Cream</option>
        <option>White</option>
        <option>Pink</option>
        <option>Green</option>
        <option>Yellow</option>
        <option>Orange</option>
        <option>Brown</option>
        <option>Denim</option>
        <option>Metalic</option>
        <option>Multi</option>
        <option>Purple</option>
        <option>Orange</option>
        <option>Red</option>
        </select>
        
        <div class="button-div">
            <button type="submit">Add to My Closet</button>
        </div>
    </form>
</div>

<style>
    .form{
        padding-top: 15px; 
    }

    .form-inputs{
        display: flex;
        flex-direction: column;
        align-items: center;
    }

</style>