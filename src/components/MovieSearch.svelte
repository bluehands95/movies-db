<script>
	import { goto } from '$app/navigation';
	import { fly } from 'svelte/transition';

	let query = '';
	let active = false;

	function cancelInactive() {
		if (query) {
			active = true;
		} else {
			active = false;
		}
	}

	function submitSearch() {
		goto('/search/' + query);
	}
</script>

<form on:submit|preventDefault={submitSearch} class="search">
	{#if !active}
		<label in:fly={{ y: -10, duration: 300 }} out:fly={{ y: -10, duration: 300 }} for="search_movie"
			>Search Movie</label
		>
	{/if}
	<input
		on:blur={cancelInactive}
		on:focus={() => (active = true)}
		bind:value={query}
		name="search_movie"
		type="text"
		id="search-bar"
	/>
	{#if query}
		<button>Search</button>
	{/if}
</form>

<style>
	form {
		margin-left: 2rem;
	}
	button {
		background-color: white;
		color: #1e1e1e;
		padding: 0.5rem;
		border: 1px solid #1e1e1e;
		outline: none;
		cursor: pointer;
	}
	input {
		border: none;
		border-bottom: 1px solid #1e1e1e;
		padding: 0.5rem;
		background-color: white;
		margin: 0.3rem;
	}
	input:focus {
		outline: none;
	}
</style>
