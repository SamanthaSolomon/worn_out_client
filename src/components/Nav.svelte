<script>
   //library imports
   import { Router, Route, Link } from "svelte-navigator"
</script>

<nav>
   <Link to="/addnew" class="pure-button">Add New</Link>
   <Link to="/dashboard" class="pure-button">Worn</Link>
   <Link to="/closet" class="pure-button">Closet</Link>
   <Link to="/about" class="pure-button">About</Link>
</nav>


<style>
   nav{
      text-align: center;
      margin-top: 3rem;
   }
</style>