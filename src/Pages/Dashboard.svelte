<script>
    //imports
    import WornMost from '../components/WornMost.svelte'
    import WornLeast from '../components/WornLeast.svelte'
    import Header from '../components/Header.svelte'
</script>


<div class="dashboard">
    <Header />
    <h2>Dashboard</h2>
    <WornMost />
    <WornLeast />
</div>
