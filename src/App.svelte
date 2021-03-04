<script>
	// imports
	import Nav from './components/Nav.svelte'
	import Header from './components/Header.svelte'
	import Closet from './components/Closet.svelte'

	// form
	const categories = [
		{id: 1, text: "Bottom"},
		{id: 2, text: "Top"},
		{id: 3, text: "Onepeice"},
		{id: 4, text: "Accessory"},
		{id: 5, text: "Outerwear"}
	]
</script>

<main>
	<h1>WornOut</h1>
	<h2>Today I wore</h2>
	<form>
		<select>
			{#each categories as category}
			<option value={category}>{category.text}
			</option>
			{/each}
		</select>
	</form>
	<Nav />
</main>

<style>
	main{
		text-align: center;
	}

	h1 {
		color: black;
	}
</style>