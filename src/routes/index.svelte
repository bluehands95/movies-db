<script context="module">
	const api = 'ea3bd0fc63f0505b9b631c1de569bc4f';
	export async function load({ fetch }) {
		const res = await fetch(
			` https://api.themoviedb.org/3/movie/popular?api_key=${api}&language=en-US&page=1`
		);
		const data = await res.json();
		// console.log(data);
		if (res.ok) {
			return {
				props: { popular: data.results }
			};
		}
	}
</script>

<script>
	import PopularMovies from '../components/PopularMovies.svelte';
	import MovieSearch from '../components/MovieSearch.svelte';
	import { fly } from 'svelte/transition';
	export let popular;
</script>

<section in:fly={{ y: -10, duration: 500 }} out:fly={{ y: -10, duration: 500 }}>
	<MovieSearch />
	<PopularMovies {popular} />
</section>
