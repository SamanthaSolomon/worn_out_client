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


//routing
	let page

	router('/', () => page = Home)
	router('/form', () => page = Form)
	// router ('/dashboard', () => page = Dashboard)
	router('/closet', () => page = Closet)
	// router ('/About', () => page = About)
	router('/item/:id', () => page = Item)

	router.start()

let url = 'https://damp-peak-94577.herokuapp.com/users/1/items'

//Get all items
let items = []
onMount( async () => {
    const response = await fetch(url)
    items = await response.json()
})

//Show details of one item
let item = {}
const getOneItem = async (id) => {
	const response = await fetch(url + `/${id}`)
	item = await response.json()
}

//Catch dispatch from WoreIt handleClick and update wear count
const handleCount = (e) => {
	const { wear_count, id} = e.detail
	let updatedItem = {...item}
		 updatedItem.wear_count++

	//Put updated wear count data
	const addWearCount = async () => {
		const response = await fetch (url + `/${item.id}`, {
			method: "PUT",
			headers: {
				"Content-Type" : "application/json"
			},
			body: JSON.stringify(updatedItem)
		})
		if(response.ok){
			const result = await response.json()
			getOneItem(updatedItem.id)
		}
	}
	addWearCount()
}




</script>



<main>
	{#if page === Home}
		<Home />
	{/if}
	{#if page === Form}
		<Form />
	{/if}
	{#if page === Closet}
		<Closet {items} {getOneItem}/>
	{/if}
	{#if page === Item}
		<Item item={item} on:addCount={handleCount} />
	{/if}
	<Nav />
</main>


<style>
	
</style>