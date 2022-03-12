<script lang="ts" context="module">
	export async function load({ fetch, params }) {
		const res = await fetch(
			`https://api.themoviedb.org/3/search/movie?sort_by=popularity.desc&api_key=23c428e5e6e883031294f63d0e90e3ce&query=${params.id}&include_adult=false&page=1`
		);

		const data = await res.json();

		if (res.ok) {
			return {
				props: { searchedMovie: data.results }
			};
		}
	}
</script>
