<script>
//libraries
	import router from 'page'
	import { onMount } from "svelte"

// imports
	import Nav from './components/Nav.svelte'
	import Home from './Pages/Home.svelte'
	// import Dashboard from './Pages/Dashboard.svelte'
	// import About from './Pages/About.svelte'
	import Closet from './Pages/Closet.svelte'
	import Form from './Pages/Form.svelte'
	import Item from './Pages/Item.svelte'
import AddUpdateButton from './components/AddUpdateButton.svelte'

//routing
	let page

	router('/', () => page = Home)
	router('/form', () => page = Form)
	// router ('/dashboard', () => page = Dashboard)
	router('/closet', () => page = Closet)
	// router ('/About', () => page = About)
	router('/item/:id', () => page = Item)

	router.start()


//get all items
let items = []

onMount( async () => {
    const response = await fetch('https://damp-peak-94577.herokuapp.com/users/1/items')
    items = await response.json()

})
</script>



<main>
	{#if page === Home}
		<Home />
	{/if}
	{#if page === Form}
		<Form />
	{/if}
	{#if page === Closet}
		<Closet {items}/>
	{/if}
	{#if page === Item}
		<Item />
	{/if}
	<Nav />
</main>


<style>
	
</style>