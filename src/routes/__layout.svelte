<script>
	import Navbar from '../components/Navbar.svelte';

	import '../global.css';
</script>

<svelte:head>
	<title>Svelte Movies | Find All Movies</title>
</svelte:head>

<Navbar />

<slot />

<footer>
	<p>&copy; Copyright 2022 | Svelte MoviesDB</p>
</footer>

<style>
	footer {
		color: white;
		text-align: center;
		padding: 2rem;
	}
</style>
