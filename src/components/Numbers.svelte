<script>
    const nums = [1,2,3,4]
</script>

{#if nums.length > 5}
{#each nums as num}
<h2>{num}</h2>
{/each}
{:else}
<ul>
{#each nums as num}
    <li>{num}</li>
{/each}
</ul>
{/if}
