
<script>
  import Router, {location, link} from 'svelte-spa-router';

  import Shows from './Pages/Shows.svelte';
  import Add from './Pages/Add.svelte';
  import Navbar from './Components/Navbar.svelte';
  import Edit from './Pages/Edit.svelte';
</script>


<Navbar />
<div class="container mt-5">
<Router routes={{
	'/': Shows,
  '/add' : Add,
  '/edit/:id' : Edit

}} />
</div>



