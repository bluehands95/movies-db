<script context="module">
	export async function load({ fetch, params }) {
		const api = 'ea3bd0fc63f0505b9b631c1de569bc4f';
		const res = await fetch(
			`https://api.themoviedb.org/3/search/movie?api_key=${api}&language=en-US&query=${params.id}&page=1&include_adult=false`
		);
		const data = await res.json();
		if (res.ok) {
			return {
				props: { searchMovie: data.results }
			};
		}
	}
</script>

<script>
	import MovieCard from '../../components/MovieCard.svelte';
	export let searchMovie;
</script>

<div class="searched">
	{#each searchMovie as movie}
		<MovieCard {movie} />
	{/each}
</div>

<style>
	.searched {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
		grid-column: 1rem;
	}
</style>
