<script>
    import { createEventDispatcher } from 'svelte';

    const dispatch = createEventDispatcher();

	export let name;
	export let points;
	let showControls = false;

	const addPoint = () => (points++);
	const removePoint = () => (points--);
    const toogleControl = () => (showControls = !showControls);
    const deletePlayer = () => dispatch("deleteplayer", name);
</script>

<style>
	h1 {
		color: #204f6e;
	}
	h3 {
		margin-bottom: 10px;
	}
</style>

	<div class="card">
        <h1>{name}</h1>
        <button class="btn btn-danger btn-sm" on:click={deletePlayer}>x</button>
		<h3>Points: {points}</h3>
		<button class="btn btn-sm" on:click={toogleControl}>{#if showControls}-{:else}+{/if}</button>
		{#if showControls}
			<button class="btn" on:click={addPoint}>+1</button>
			<button class="btn btn-dark" on:click={removePoint}>-1</button>
			<input type="number" bind:value={points}>
		{/if}
	</div>
