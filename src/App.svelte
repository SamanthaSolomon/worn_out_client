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
	router('/item', () => page = Item)

	router.start()
</script>



<main>
	<svelte:component this={page} {params} />
	<Nav />
</main>


<style>
	
</style>