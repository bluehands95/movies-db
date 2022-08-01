<script>
	export let popular;
	import MovieCard from './MovieCard.svelte';
</script>

<h1>Popular Movies</h1>
<div class="popular-movies">
	{#each popular as movie}
		<MovieCard {movie} />
	{/each}
</div>

<style>
	* {
		margin: 1rem;
		padding: 0;
	}
	.popular-movies {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
		grid-column: 1rem;
	}
</style>
