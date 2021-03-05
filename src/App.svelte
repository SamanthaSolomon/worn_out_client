<script>
//libraries
	import router from 'page'

// imports
	import Nav from './components/Nav.svelte'
	import Home from './Pages/Home.svelte'
	import Dashboard from './Pages/Dashboard.svelte'
	import About from './Pages/About.svelte'
	import Closet from './Pages/Closet.svelte'
	import Form from './Pages/Form.svelte'

//routing
	let page
	let params

	router('/', () => page = Home)
	router('/form/:action', (ctx, next) => {
		params = ctx.params
		next()
	}, () => page = Form)
	router ('/dashboard', () => page = Dashboard)
	router ('/closet', () => page = Closet)
	router ('/About', () => page = About)

	router.start()
</script>



<main>
	<svelte:component this={page} {params} />
	<Nav />
</main>


<style>
	
</style>