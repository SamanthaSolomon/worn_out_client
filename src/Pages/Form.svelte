<script>
    //libraries
    import { createForm } from "svelte-forms-lib"

    //imports
    import AddUpdateButton from '../components/AddUpdateButton.svelte'
    import Header from '../components/Header.svelte'

    //form
    const { form, handleChange, handleSubmit } = createForm({
      initialValues: {
        title: "",
        name: "",
        email: ""
      },
      onSubmit: values => {
        alert(JSON.stringify(values));
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
        on:change={handleChange}
        bind:value={$form.img}
        />

    <label for="category">Category</label>
    <select
      id="category"
      name="category"
      on:change={handleChange}
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
      on:change={handleChange}
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
      on:change={handleChange}
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
      on:change={handleChange}
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
  </form>

    <AddUpdateButton/>
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