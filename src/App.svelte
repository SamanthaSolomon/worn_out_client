<script>
	import Header from './components/Header.svelte'
	import Footer from './components/Footer.svelte'
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
	<h2>Closet count: {count}</h2>
	<button on:click={addOne}>Click to add</button>
	<h2>{input}</h2>
	<input type="text" bind:value={input}/>
	<button on:click={submit}>Submit</button>
	<Footer/>
</main>

<style>
	h1 {
		color: aqua
	}
</style>