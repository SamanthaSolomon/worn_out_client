<script>
    //libraries
    import { createForm } from "svelte-forms-lib"

    //imports
    import AddUpdateButton from '../components/AddUpdateButton.svelte'
    import Header from '../components/Header.svelte'

    //form
    let result

    const { form, handleChange, handleSubmit } = createForm({
      initialValues: {
        img: "",
        category: "",
        style: "",
        use: "",
        color: ""
      },
      //post new item
      onSubmit: async (value) => {
          const res = await fetch('https://damp-peak-94577.herokuapp.com/users/1/items', {
              method: 'POST', 
              body: JSON.stringify(value)
            })
          const json = await res.json()
          result = JSON.stringify(json)
      }
    });
    
  </script>



<div class="form">
    <Header />
    <p>Add new item to my closet</p>

    <form class="form-inputs" on:submit={handleSubmit}>
        <label for="img">Image (url)</label>
        <input id="img" 
        name="img"
        bind:value={$form.img}
        />

    <label for="category">Category</label>
    <select
      id="category"
      name="category"
      bind:value={$form.category}>
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
      bind:value={$form.style}>
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
    </select>

    <label for="use">Use</label>
    <select
      id="use"
      name="use"
      bind:value={$form.use}>
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
      bind:value={$form.color}>
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
    
     <button type="button" on:click={handleSubmit}>Add</button>
    </form>

    <pre>{result}</pre>

</div>

<style>
    .form{
        text-align: center;
    }

    .form-inputs{
        display: flex;
        flex-direction: column;
        align-items: center;
    }

    input, select{
        width: 20%;
        margin-bottom: 1rem
    }
</style>