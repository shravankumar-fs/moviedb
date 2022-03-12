<script lang="ts" context="module">
	export async function load({ fetch }) {
		const res = await fetch(
			'https://api.themoviedb.org/3/discover/movie?sort_by=popularity.desc&api_key=23c428e5e6e883031294f63d0e90e3ce&page=1'
		);

		const data = await res.json();

		if (res.ok) {
			return {
				props: { popular: data.results }
			};
		}
	}
</script>

<script lang="ts">
	import { fly } from 'svelte/transition';
	import PopularMovies from '../components/PopularMovies.svelte';
	import SearchMovie from '../components/SearchMovie.svelte';
	export let popular;
</script>

<section in:fly={{ x: 100, duration: 500 }} out:fly={{ x: -100, duration: 500, delay: 500 }}>
	<SearchMovie />
	<PopularMovies {popular} />
</section>
