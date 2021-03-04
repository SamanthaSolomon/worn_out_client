<script>
	//library imports
	import { Router, Route, Link } from "svelte-navigator"
	// imports
	import Nav from './components/Nav.svelte'
	import Home from './Pages/Home.svelte'

</script>

<Router>
	<main>
		<Home />
		<Nav />
	</main>
</Router>

<style>
	
</style>