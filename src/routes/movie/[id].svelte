<script lang="ts" context="module">
	export async function load({ fetch, params }) {
		const res = await fetch(
			`https://api.themoviedb.org/3/movie/${params.id}?api_key=23c428e5e6e883031294f63d0e90e3ce`
		);

		const movieDetail = await res.json();

		if (res.ok) {
			return {
				props: { movieDetail }
			};
		}
	}
</script>

<script lang="ts">
	export let movieDetail;
</script>

<div class="movie-details">
	<div class="img-container">
		<img
			src={`https://image.tmdb.org/t/p/original/` + movieDetail.backdrop_path}
			alt={movieDetail.title}
		/>
	</div>
	<div class="txt-container">
		<h1>{movieDetail.title}</h1>
		<p class="overview" />
	</div>
</div>
