<script>
	import Header from './components/Header.svelte'
	import Footer from './components/Footer.svelte'
	import Numbers from './components/Numbers.svelte'
	import Mount from './components/Mount.svelte'

	export let name;
	let count = 0;
	const addOne =() => {
		count += 1
	}
	let input = "Wish list"
	const submit = () => {
		alert(input)
	}
</script>

<main>
	<Header myProp={input}/>
	<h1>{name}!</h1>
	<Mount/>
</main>

<style>
	h1 {
		color: aqua
	}
</style>