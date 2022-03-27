<script>
	import { each } from 'svelte/internal';
	import MovieCard from './MovieCard.svelte';

	export let popular;
	console.log(popular[0]);
</script>

<section class="popular-movies">
	<h2>Popular Movies</h2>
	<div class="movies">
		{#each popular as movie}
			<MovieCard {movie} />
		{/each}
	</div>
</section>

<style>
	.movies {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
		grid-column-gap: 1rem;
		grid-row-gap: 2rem;
	}

	h2 {
		padding-left: 1rem;
	}
</style>
