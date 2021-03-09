<script>
//libraries
	import router from 'page'

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
	let params

	router('/', () => page = Home)
	router('/form', () => page = Form)
	// router ('/dashboard', () => page = Dashboard)
	router('/closet', () => page = Closet)
	// router ('/About', () => page = About)
	router('/item/:id', () => page = Item)

	router.start()
</script>



<main>
	{#if page === Home}
		<Home />
	{/if}
	{#if page === Form}
		<Form />
	{/if}
	{#if page === Closet}
		<Closet />
	{/if}
	{#if page === Item}
		<Item />
	{/if}
	<Nav />
</main>


<style>
	
</style>