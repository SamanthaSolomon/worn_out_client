<script>
    //imports
    import AddUpdateButton from '../components/AddUpdateButton.svelte'
    import Header from '../components/Header.svelte'

    //call for one item
    let item = []
    let url = 'https://damp-peak-94577.herokuapp.com/users/1/items'

    onMount( async () => {
        const response = await fetch('url')
        item = await response.json()
    })



</script>



<div class="item">
    <Header />
    <h2>Item Component</h2>
    <AddUpdateButton />
    
</div>