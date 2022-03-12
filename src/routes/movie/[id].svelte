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
	import { fly } from 'svelte/transition';
</script>

<div
	class="movie-details"
	in:fly={{ x: -100, duration: 500, delay: 500 }}
	out:fly={{ x: 100, duration: 500 }}
>
	<div class="img-container">
		<img
			src={`https://image.tmdb.org/t/p/original/` + movieDetail.backdrop_path}
			alt={movieDetail.title}
		/>
	</div>
	<div class="txt-container">
		<h1>{movieDetail.title}</h1>
		<p class="overview">{movieDetail.overview}</p>
		<p>
			<span>Release : </span>{movieDetail.release_date}<br />
			<span>Budget : </span>{movieDetail.budget}<br />
			<span>Rating : </span>{movieDetail.vote_average}<br />
			<span>Runtime :</span>{movieDetail.runtime}mins <br />
		</p>
	</div>
</div>

<style>
	h1 {
		padding: 1 rem 0rem 2rem;
		text-align: center;
		color: aliceblue;
	}
	p {
		padding: 1rem 0rem;
	}
	.img-container {
		width: 100%;
	}
	img {
		width: 100%;
		border-radius: 1rem;
	}
	.movie-details {
		height: 100%;
		width: 80%;
		margin: 2rem auto;
		padding: 2rem;
		border-radius: 0.5rem;
		box-shadow: 6px 6px 8px 1px rgba(0, 0, 0, 0.3), -4px -4px 8px 1px rgba(255, 255, 255, 0.05),
			inset -1px -1px 6px 1px rgba(255, 255, 255, 0.1), inset 1px 1px 6px 1px rgba(0, 0, 0, 0.1);
		background: linear-gradient(-135deg, hsla(200, 100%, 10%, 0.9) 50%, hsla(200, 100%, 5%, 0.9));
	}
	span {
		font-weight: bold;
	}
</style>
