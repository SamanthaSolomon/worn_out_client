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

//get all items
let items = []
onMount( async () => {
    const response = await fetch(url)
    items = await response.json()
})

//see details of one item
let item = {}
const getOneItem = async (id) => {
	const thisUrl = url + `$/{id}`
	console.log('this url-', thisUrl)
	const response = await fetch(url + `/${id}`)
	item = await response.json()
	console.log('item-', item)
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
		<Item item={item} />
	{/if}
	<Nav />
</main>


<style>
	
</style>