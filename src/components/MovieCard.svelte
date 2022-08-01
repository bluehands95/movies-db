<script>
	import { fly } from 'svelte/transition';
	export let movie;
</script>

<div class="movie-card" in:fly={{ y: -10, duration: 300 }} out:fly={{ y: -10, duration: 300 }}>
	<a sveltekit:noscroll sveltekit:prefetch href={'/movie/' + movie.id}>
		<img src={'https://image.tmdb.org/t/p/w500' + movie.poster_path} alt="movie.title" />
	</a>
	<div class="description">
		<h3>{movie.title}</h3>
		<p>{movie.release_date}</p>
		<p>Rating: {movie.vote_average}</p>
	</div>
</div>

<style>
	.movie-card {
		padding: 0.75rem;
	}
	img {
		width: 90%;
		height: 50vh;
		object-fit: cover;
		border-radius: 1rem;
		margin-bottom: 1rem;
		cursor: pointer;
	}
	h3 {
		font-size: 0.9rem;
	}
	.description {
		margin-bottom: 2rem;
	}
</style>
