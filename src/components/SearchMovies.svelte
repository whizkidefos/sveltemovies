<script>
	import { goto } from '$app/navigation';
	import { fly } from 'svelte/transition';

	let inputValue = '';
	let active = false;

	const cancelInactive = () => {
		if (inputValue) {
			active = true;
		} else {
			active = false;
		}
	};

	const submitSearch = () => {
		goto('/search/' + inputValue);
	};
</script>

<form class="search" on:submit|preventDefault={submitSearch}>
	{#if !active}
		<label in:fly={{ y: -10, duration: 500 }} out:fly={{ y: -10, duration: 500 }} for="search_movie"
			>Search for a movie...</label
		>
	{/if}

	<input
		bind:value={inputValue}
		on:blur={cancelInactive}
		on:focus={() => (active = true)}
		type="text"
		name="search_movie"
		class={active ? 'selected' : ''}
	/>
	{#if inputValue}
		<button in:fly={{ x: -10, duration: 500 }} out:fly={{ x: -10, duration: 500 }}>Search</button>
	{/if}
</form>

<style>
	.search {
		position: relative;
		width: 50%;
		margin: 2rem auto;
		text-align: center;
	}

	input {
		height: 40px;
		width: 100%;
		border-radius: 2rem;
		border: none;
		outline: none;
		font-size: 1rem;
		color: rgb(255, 255, 255);
		padding: 0 1rem;
		transition: all 0.75s ease-out;
		background: rgb(63, 63, 63);
	}

	input.selected {
		background: rgb(27, 27, 27);
	}

	button {
		font-size: 0.7rem;
		padding: 0 1rem;
		background: rgb(20, 20, 20);
		color: white;
		border: none;
		font-weight: 600;
		position: absolute;
		right: 0;
		bottom: 50%;
		transform: translate(0, 50%);
		height: 40px;
		border-radius: 0 2rem 2rem 0;
		cursor: pointer;
	}

	label {
		position: absolute;
		font-size: 0.8rem;
		top: 50%;
		left: 1.3rem;
		transform: translate(0, -50%);
		pointer-events: none;
		color: azure;
	}
</style>
