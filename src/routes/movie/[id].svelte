<script context="module">
	export async function load({ fetch, params }) {
		const res = await fetch(
			`https://api.themoviedb.org/3/movie/${params.id}?api_key=${
				import.meta.env.VITE_MOVIE_API
			}&language=en-US&page=1`
		);

		const movieDetail = await res.json();

		if (res.ok) {
			return {
				props: { movieDetail }
			};
		}
	}
</script>

<script>
	export let movieDetail;
</script>

<section class="movie-detail">
	<figure class="image-container">
		<img
			src={'https://image.tmdb.org/t/p/original' + movieDetail.backdrop_path}
			alt={movieDetail.title}
		/>
		<h5>{movieDetail.vote_average}</h5>
	</figure>
	<article class="text-container">
		<h1>{movieDetail.title}</h1>
		<p class="overview">{movieDetail.overview}</p>
		<p class="meta">
			<span>Release Date:</span>
			<span>{movieDetail.release_date}</span> <br />
			<span>Budget: ${movieDetail.budget}</span> <br />
			<span>Rating: {movieDetail.vote_average}</span> <br />
			<span>Runtime: {movieDetail.runtime} mins</span>
		</p>
	</article>
</section>

<style>
	article {
		padding: 1rem 0rem;
	}

	h1 {
		padding: 0;
		font-size: 3rem;
	}

	p {
		padding: 0.3rem 0;
	}

	figure {
		position: relative;
	}

	figure h5 {
		position: absolute;
		bottom: 4rem;
		right: 3rem;
		width: 100px;
		height: 100px;
		border-radius: 100%;
		background: black;
		color: white;

		display: flex;
		align-items: center;
		justify-content: center;
		font-weight: 600;
	}

	img {
		border-radius: 1rem;
		width: 100%;
	}

	.movie-detail {
		margin: 2rem 10%;
	}

	span {
		font-weight: bold;
	}

	@media (max-width: 580px) {
		h1 {
			font-size: 1.5rem;
		}

		figure h5 {
			width: 50px;
			height: 50px;
			bottom: 1rem;
			right: 0.5rem;
		}
	}
</style>
