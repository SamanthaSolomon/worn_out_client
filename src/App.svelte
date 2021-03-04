<script>
	import Header from './components/Header.svelte'
	import Footer from './components/Footer.svelte'
	export let name;
</script>

<main>
	<Header/>
	<h1>{name}!</h1>
	<p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>
	<Footer/>
</main>

<style>
</style>