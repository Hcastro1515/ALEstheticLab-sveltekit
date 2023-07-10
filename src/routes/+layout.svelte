<script>
	import '../app.postcss';
	import Navbar from '../components/navbar.svelte';
</script>

<Navbar />
<main class="mx-auto w-4/5">
	<slot />
</main>
