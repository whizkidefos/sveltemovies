<script context="module">
	export async function load({ fetch, params }) {
		const res = await fetch(
			`
https://api.themoviedb.org/3/search/movie?api_key=${
				import.meta.env.VITE_MOVIE_API
			}&language=en-US&query=${params.id}&page=1&include_adult=false`
		);

		const data = await res.json();

		if (res.ok) {
			return {
				props: { searchedMovie: data.results }
			};
		}
	}
</script>

<script>
	import MovieCard from '../../components/MovieCard.svelte';

	export let searchedMovie;
</script>

<section class="search-result">
	{#each searchedMovie as movie}
		<MovieCard {movie} />
	{/each}
</section>

<style>
	.search-result {
		max-width: 50%;
		width: 100%;
		margin: 0 auto;
	}
</style>
