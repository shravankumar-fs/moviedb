<script lang="ts">
	export let movie;
</script>

<div class="movie-card">
	<a sveltekit:noscroll sveltekit:prefetch href={'/movie/' + movie.id}>
		<img src={`https://image.tmdb.org/t/p/w500/` + movie.poster_path} alt={movie.title} />
	</a>
	<div class="description">
		<h2>{movie.title}</h2>
		<p>{movie.release_date}</p>
	</div>
</div>

<style>
	img {
		width: 100%;
		height: 30vh;
		object-fit: cover;
		border-radius: 1rem;
		margin-bottom: 1rem;
	}
	h2 {
		font-size: 0.9rem;
	}
	.description {
		height: 5vh;
	}
	p {
		font-size: 0.7rem;
	}
	.movie-card {
		display: flex;
		flex-direction: column;
		justify-content: space-around;
		padding: 2rem;
		border-radius: 0.5rem;
		box-shadow: 6px 6px 8px 1px rgba(0, 0, 0, 0.3), -4px -4px 8px 1px rgba(255, 255, 255, 0.05),
			inset -1px -1px 6px 1px rgba(255, 255, 255, 0.1), inset 1px 1px 6px 1px rgba(0, 0, 0, 0.1);
		background: linear-gradient(-45deg, hsla(200, 100%, 10%, 0.9) 80%, hsla(200, 100%, 5%, 0.9));
	}
</style>
