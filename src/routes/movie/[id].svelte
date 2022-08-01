<script context="module">
	export async function load({ fetch, params }) {
		const api = 'ea3bd0fc63f0505b9b631c1de569bc4f';
		const res = await fetch(
			` https://api.themoviedb.org/3/movie/${params.id}?api_key=${api}&language=en-US`
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

<div class="movie-details">
	<div class="img">
		<img
			src={'https://image.tmdb.org/t/p/original' + movieDetail.backdrop_path}
			alt={movieDetail.id}
		/>
	</div>
	<div class="txt">
		<h1>{movieDetail.title}</h1>
		<p>{movieDetail.overview}</p>
		<p>
			<span>Release Date: </span>
			{movieDetail.release_date} <br />
			<span>Popularity:</span>
			{movieDetail.popularity} <br />
			<span>Runtime: </span>
			{movieDetail.runtime}minutes <br />
			<span>Rating: </span>
			{movieDetail.vote_average} <br />
			<span>Adult: </span>
			{movieDetail.adult} <br />
		</p>
	</div>
</div>

<style>
	.movie-details {
		display: flex;
		flex-direction: column;
		align-items: center;
	}
	img {
		width: 100%;
		height: 50vh;
		object-fit: cover;
		border-radius: 1rem;
		margin-bottom: 1rem;
	}
</style>
