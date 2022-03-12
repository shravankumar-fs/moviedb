<script lang="ts">
	let search = '';
	import { goto } from '$app/navigation';

	function submitSearch() {
		goto('/search/' + search);
	}
</script>

<form class="search" on:submit|preventDefault={submitSearch}>
	<input
		class={search != '' ? 'selected' : ''}
		name="search_movie"
		type="text"
		bind:value={search}
	/>
	<label for="search_movie">Search Movie</label>
	{#if search}
		<button>Search</button>
	{/if}
</form>

<style>
	.search {
		position: relative;
		width: 30%;
		margin: 1rem;
	}
	button {
		font-size: 0.7rem;
		padding: 0rem 1rem;
		background: rgb(96, 110, 201);
		color: #fff;
		font-weight: bold;
		border: none;
		position: absolute;
		bottom: 50%;
		right: 0;
		transform: translate(0, 50%);
		height: 100%;
		border-top-right-radius: 10px;
		border-bottom-right-radius: 10px;
		cursor: pointer;
	}
	input {
		width: 100%;
		border: none;
		font-size: 1rem;
		font-family: 'Kanit', sans-serif;
		outline: none;
		color: rgb(255, 255, 255);
		padding: 0.5rem 0.1rem;
		transition: background 0.75s ease-out;
		font-weight: bold;
		background: rgb(63, 63, 63);
		border-radius: 10px;
		padding: 1rem;
	}
	label {
		position: absolute;
		font-size: 0.8rem;
		top: 50%;
		left: 0;
		transform: translate(0, -50%);
		pointer-events: none;
		color: #fff;
		padding: 0rem 1rem;
		transition: 0.3s ease-in-out;
	}
	input:focus ~ label {
		top: -20%;
		color: rgb(63, 63, 63);
	}
	input.selected {
		background-color: rgb(40, 40, 40);
	}
</style>
