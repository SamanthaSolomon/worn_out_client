<script>
//component imports
import Find from "../components/Find.svelte"
import AddUpdateButton from "../components/AddUpdateButton.svelte"

// dropdown
	const categories = [
		{id: 1, text: "Bottom"},
		{id: 2, text: "Top"},
		{id: 3, text: "Onepeice"},
		{id: 4, text: "Accessory"},
		{id: 5, text: "Outerwear"}
		]
</script>

<div class="home">
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
    <Find />
    <button>Wore It</button>
</div>

<style>
	.home{
		text-align: center;
	}

	h1 {
		color: black;
	}

/* Tablet styles */
@media only screen and (min-width: 768px){

	.home{
		padding-top: 12%;
	}
}

/* Desktop styles */
@media only screen and (min-width: 1440px){

	.home{
		padding-top: 8%;
	}


}
</style>