<script>
	export let movie;
</script>

<article class="movie">
	<a sveltekit:noscroll sveltekit:prefetch href={'/movie/' + movie.id}>
		<img src={'https://image.tmdb.org/t/p/w500' + movie.poster_path} alt={movie.title} />
	</a>
	<h3>{movie.title}</h3>
	<p>{movie.release_date}</p>
	<small>{movie.vote_average}</small>
</article>

<style>
	.movie {
		display: flex;
		flex-direction: column;
		justify-content: center;
		padding: 1rem;
		position: relative;
	}

	img {
		border-radius: 2rem;
		width: 100%;
		height: 40vh;
		object-fit: cover;
		margin-bottom: 1rem;
	}

	h3 {
		font-size: 0.9rem;
	}

	small {
		position: absolute;
		bottom: 4rem;
		right: 3rem;
		width: 50px;
		height: 50px;
		border-radius: 100%;
		background: black;
		color: white;

		display: flex;
		align-items: center;
		justify-content: center;
		font-weight: 600;
	}
</style>
