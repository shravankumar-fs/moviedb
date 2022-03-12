<script lang="ts">
	let search = '';
	import { goto } from '$app/navigation';
	import { fly } from 'svelte/transition';

	function submitSearch() {
		goto('/search/' + search);
	}
	let active = false;
	$: {
		active = search != '';
	}
</script>

<form class="search" on:submit|preventDefault={submitSearch}>
	<input class={active ? 'selected' : ''} name="search_movie" type="text" bind:value={search} />
	{#if !active}
		<label for="search_movie" out:fly={{ y: -30, duration: 500 }} in:fly={{ y: 30, duration: 500 }}
			>Search Movie</label
		>
	{/if}
	{#if search}
		<button out:fly={{ x: 0, duration: 500 }} in:fly={{ x: 30, duration: 500 }}>Search</button>
	{/if}
</form>

<style>
	.search {
		position: relative;
		width: 40%;
		margin: 1rem 0;
		overflow-x: hidden;
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
		font-family: 'Montserrat', sans-serif;
		outline: none;
		color: lightseagreen;
		padding: 0.5rem 0.1rem;
		transition: background 0.75s ease-out;
		font-weight: bold;
		background: linear-gradient(135deg, hsla(200, 100%, 10%, 0.9) 50%, hsla(200, 100%, 5%, 0.9));
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
		color: lightseagreen;
		padding: 0rem 1rem;
		transition: 0.8s ease-in-out;
	}

	input.selected {
		background-color: rgb(40, 40, 40);
	}

	@media only screen and (max-width: 600px) {
		.search {
			width: 100%;
		}
	}
</style>
